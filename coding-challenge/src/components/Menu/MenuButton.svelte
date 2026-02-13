<script lang="ts">
    import { getContext } from "svelte";
    import { ChevronsUpDown } from "lucide-svelte";
    import Button from "../Button/Button.svelte";

    const { open, toggle, selectedLabel, buttonId, listboxId, setButtonEl } = getContext<{
        open: import("svelte/store").Writable<boolean>;
        toggle: () => void;
        selectedLabel: import("svelte/store").Writable<string | null>;
        buttonId: string;
        listboxId: string;
        setButtonEl: (el: HTMLButtonElement | null) => void;
    }>("menu");

    let buttonEl: HTMLButtonElement | null = null;
    $: if (buttonEl != null) setButtonEl(buttonEl);
</script>

<Button
    bind:element={buttonEl}
    type="button"
    id={buttonId}
    aria-haspopup="listbox"
    aria-expanded={$open}
    aria-controls={listboxId}
    aria-label="Select a product"
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
