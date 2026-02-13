<script lang="ts">
    import { getContext } from "svelte";
    import Button from "../Button/Button.svelte";

    const { toggle } = getContext<{ toggle: () => void }>('menuContext');
</script>

<Button
    type="button"
    on:click={toggle}
>
    <slot />
</Button>

