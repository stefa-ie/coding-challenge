<script lang="ts">
    /**
     * Button – reusable trigger; supports optional focus ring and element binding for accessibility.
     */
    import { onMount, tick } from "svelte";

    export let onClick = () => {};
    export let type: any = "button";
    export let disabled: boolean = false;
    /** Visual variant: primary (filled) or secondary (outline/ghost). */
    export let variant: "primary" | "secondary" = "secondary";
    /** Size: small, middle (default), or large. */
    export let size: "small" | "middle" | "large" = "middle";
    /** When true, show 2px #B0B0B0 outline on focus only (not hover). Set false e.g. when dropdown is open. */
    export let showFocusStroke = true;
    /** Optional: bind to get the underlying button DOM element (e.g. for focus return). */
    export let element: HTMLButtonElement | null = null;
    /** When true, button receives focus when the page loads (for barrier-free first interaction). */
    export let autofocus = false;
    /** Optional label; when set, used as button content instead of the default slot. */
    export let label: string | undefined = undefined;

    const base = "w-full rounded-lg flex items-center justify-between text-left cursor-pointer font-medium";
    const stroke = "focus:outline-2 focus:outline-[#B0B0B0] focus:outline-offset-0";

    // Style maps keyed by variant/size (used in reactive assignments below)
    const variantClasses = {
        primary: "bg-gray-600 text-white hover:bg-gray-700 disabled:bg-gray-400 disabled:text-gray-200",
        secondary: "bg-white hover:bg-gray-50 text-gray-800 disabled:bg-gray-100 disabled:text-gray-400",
    };
    const sizeClasses = {
        small: "h-8 px-3 text-sm",
        middle: "h-[40px] px-4 text-base",
        large: "h-12 px-5 text-lg",
    };

    $: variantClass = variantClasses[variant];
    $: sizeClass = sizeClasses[size];

    onMount(() => {
        if (!autofocus) return;
        tick().then(() => element?.focus());
    });
</script>

<button
    bind:this={element}
    type={type}
    class="{base} {variantClass} {sizeClass} {showFocusStroke ? stroke : ''}"
    disabled={disabled}
    on:click={onClick}
    {...$$restProps}>
    {#if label != null && label !== ''}
        {label}
    {:else}
        <slot />
    {/if}
</button>
