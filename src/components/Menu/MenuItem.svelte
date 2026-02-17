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

<!-- Listbox option; highlight (#E1FF2C) when focused or hovered -->
<div
    role="option"
    id={optionId}
    tabindex="-1"
    aria-selected={selected}
    class="menu-item w-full h-10 flex items-center justify-center text-gray-800 cursor-pointer"
    on:click={choose}
    on:keydown={(e) => e.key === 'Enter' && choose()}>
    <div class="w-[238px] h-full rounded-[4px] flex items-center justify-between pl-[9px] pr-2 {focused && !selected ? 'bg-[#E1FF2C]' : ''} hover:bg-[#E1FF2C]">
        <span><slot /></span>
        {#if selected}
            <Check class="w-4 h-4 text-gray-600 shrink-0" />
        {:else}
            <span class="w-4 h-4 shrink-0" aria-hidden="true"></span>
        {/if}
    </div>
</div>
