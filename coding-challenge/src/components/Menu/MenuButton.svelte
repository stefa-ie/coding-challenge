<script lang="ts">
    import { getContext } from "svelte";
    import { ChevronsUpDown } from "lucide-svelte";
    import Button from "../Button/Button.svelte";

    const { open, toggle, selectedLabel } = getContext<{
        open: import("svelte/store").Writable<boolean>;
        toggle: () => void;
        selectedLabel: import("svelte/store").Writable<string | null>;
    }>("menu");
</script>

<Button
    type="button"
    onClick={toggle}
    showFocusStroke={!$open}
>
    {#if $selectedLabel}
        <span class="font-normal text-base text-gray-800">{$selectedLabel}</span>
    {:else}
        <slot />
    {/if}
    <ChevronsUpDown class="w-4 h-4 text-gray-500 shrink-0" />
</Button>
