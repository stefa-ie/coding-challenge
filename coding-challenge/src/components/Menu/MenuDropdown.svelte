<script lang="ts">
    import { getContext } from "svelte";
    import type { Writable } from "svelte/store";

    const { open } = getContext<{ open: Writable<boolean> }>("menu");
</script>

{#if $open}
    <div class="absolute top-full left-0 right-0 w-[250px] h-[132px] mt-1 rounded-lg bg-white px-[6px] py-[3px] shadow-lg border border-gray-200 flex flex-col gap-[3px]">
        <slot />
    </div>
{/if}
