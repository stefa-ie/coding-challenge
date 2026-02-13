<script lang="ts">
    import { getContext } from "svelte";
    import { ChevronsUpDown } from "lucide-svelte";
    import Button from "../Button/Button.svelte";

    const { toggle } = getContext<{ toggle: () => void }>('menu');
</script>

<Button
    type="button"
    on:click={toggle}
>
    <slot />
    <ChevronsUpDown class="w-20 h-20 text-black" />
</Button>
