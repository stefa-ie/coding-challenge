<script lang="ts">
    /**
     * MenuItem – one option in the listbox; click or Enter to select.
     * Registers with Menu for stable id/index (accessibility).
     */
    import { getContext } from "svelte";
    import { Check } from "lucide-svelte";

    /** Value stored when this option is selected; also used for ARIA. */
    export let value = "";

    const { select, selectedLabel, registerOption, focusedIndex } = getContext<{
        select: (label: string) => void;
        selectedLabel: import("svelte/store").Writable<string | null>;
        registerOption: (value: string) => { id: string; index: number };
        focusedIndex: import("svelte/store").Writable<number>;
    }>("menu");

    const { id: optionId, index } = registerOption(value);

    $: selected = $selectedLabel === value;
    $: focused = $focusedIndex === index;

    function choose() {
        if (value) select(value);
    }
</script>

<!-- role="option" + id for listbox aria-activedescendant; spacer when not selected keeps layout even -->
<div
    role="option"
    id={optionId}
    tabindex="-1"
    aria-selected={selected}
    class="menu-item w-[238px] h-10 rounded px-4 text-gray-800 cursor-pointer flex items-center justify-between hover:bg-[#E1FF2C] {focused ? 'bg-[#E1FF2C]' : ''}"
    on:click={choose}
    on:keydown={(e) => e.key === 'Enter' && choose()}>
    <span><slot /></span>
    {#if selected}
        <Check class="w-4 h-4 text-gray-600 shrink-0" />
    {:else}
        <span class="w-4 h-4 shrink-0" aria-hidden="true"></span>
    {/if}
</div>
