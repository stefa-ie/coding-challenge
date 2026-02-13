<script lang="ts">
    import { getContext } from "svelte";
    import { Check } from "lucide-svelte";

    export let value = "";

    const { select, selectedLabel } = getContext<{
        select: (label: string) => void;
        selectedLabel: import("svelte/store").Writable<string | null>;
    }>("menu");

    $: selected = $selectedLabel === value;

    function choose() {
        if (value) select(value);
    }
</script>

<div
    role="menuitem"
    tabindex="0"
    class="menu-item w-[238px] h-10 rounded px-4 text-sm text-gray-800 cursor-pointer flex items-center justify-between hover:bg-[#E1FF2C] {selected ? 'bg-gray-50' : ''}"
    on:click={choose}
    on:keydown={(e) => e.key === 'Enter' && choose()}>
    <span><slot /></span>
    {#if selected}
        <Check class="w-4 h-4 text-gray-600 shrink-0" />
    {:else}
        <span class="w-4 h-4 shrink-0" aria-hidden="true" />
    {/if}
</div>