<script lang="ts">
    import { getContext } from "svelte";
    import { tick } from "svelte";
    import type { Writable } from "svelte/store";

    const {
        open,
        listboxId,
        buttonId,
        focusedIndex,
        options,
        handleListboxKeydown,
    } = getContext<{
        open: Writable<boolean>;
        listboxId: string;
        buttonId: string;
        focusedIndex: Writable<number>;
        options: Writable<string[]>;
        handleListboxKeydown: (e: KeyboardEvent) => void;
    }>("menu");

    let listboxEl: HTMLDivElement;

    $: activeId = $options[$focusedIndex] != null ? listboxId + "-option-" + $focusedIndex : undefined;

    $: if ($open && listboxEl) {
        tick().then(() => listboxEl?.focus());
    }
</script>

{#if $open}
    <div
        bind:this={listboxEl}
        role="listbox"
        id={listboxId}
        tabindex="0"
        aria-labelledby={buttonId}
        aria-activedescendant={activeId}
        class="absolute top-full left-0 right-0 w-[250px] h-[132px] mt-1 rounded-lg bg-white px-[6px] py-[3px] shadow-lg border border-gray-200 flex flex-col gap-[3px] outline-none"
        on:keydown={handleListboxKeydown}
    >
        <slot />
    </div>
{/if}
