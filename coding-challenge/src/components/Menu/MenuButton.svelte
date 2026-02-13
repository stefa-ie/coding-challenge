<script lang="ts">
    /**
     * MenuButton – trigger that opens/closes the listbox and shows selected or placeholder.
     */
    import { getContext } from "svelte";
    import { ChevronsUpDown } from "lucide-svelte";
    import Button from "../Button/Button.svelte";

    /** When true, the trigger receives focus on load so keyboard users can open immediately (e.g. Enter). */
    export let autofocus = false;

    const { open, toggle, selectedLabel, buttonId, listboxId, setButtonEl } = getContext<{
        open: import("svelte/store").Writable<boolean>;
        toggle: () => void;
        selectedLabel: import("svelte/store").Writable<string | null>;
        buttonId: string;
        listboxId: string;
        setButtonEl: (el: HTMLButtonElement | null) => void;
    }>("menu");

    let buttonEl: HTMLButtonElement | null = null;
    // Register button ref so Menu can return focus on close (accessibility)
    $: if (buttonEl != null) setButtonEl(buttonEl);
</script>

<!-- ARIA: combobox pattern with listbox; focus stroke only when closed -->
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
    autofocus={autofocus}
>
    <!-- Selected value or placeholder from slot -->
    {#if $selectedLabel}
        <span class="font-normal text-base text-gray-800">{$selectedLabel}</span>
    {:else}
        <slot />
    {/if}
    <ChevronsUpDown class="w-4 h-4 text-gray-500 shrink-0" />
</Button>
