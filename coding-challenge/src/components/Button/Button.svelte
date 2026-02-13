<script lang="ts">
    /**
     * Button – reusable trigger; supports optional focus ring and element binding for accessibility.
     */
    import { onMount, tick } from "svelte";

    export let onClick = () => {};
    export let type: any = "button";
    export let disabled: boolean = false;
    /** When true, show 2px #B0B0B0 outline on focus only (not hover). Set false e.g. when dropdown is open. */
    export let showFocusStroke = true;
    /** Optional: bind to get the underlying button DOM element (e.g. for focus return). */
    export let element: HTMLButtonElement | null = null;
    /** When true, button receives focus when the page loads (for barrier-free first interaction). */
    export let autofocus = false;

    const base = "w-full h-[40px] rounded-lg bg-white flex items-center justify-between px-4 hover:bg-gray-50 text-left cursor-pointer font-medium";
    const stroke = "focus:outline focus:outline-2 focus:outline-[#B0B0B0] focus:outline-offset-0";

    onMount(() => {
        if (!autofocus) return;
        tick().then(() => element?.focus());
    });
</script>

<button
    bind:this={element}
    type={type}
    class="{base} {showFocusStroke ? stroke : ''}"
    disabled={disabled}
    on:click={onClick}
    {...$$restProps}>
    <slot />
</button>
