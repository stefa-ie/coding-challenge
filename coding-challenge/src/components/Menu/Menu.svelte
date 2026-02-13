<script lang="ts">
    import { setContext }  from "svelte";
    import { writable, type Writable } from "svelte/store";

    const open: Writable<boolean> = writable(false);

    function toggle() {
        open.update(v => !v);
    }

    // Providing values to children
    setContext("menu", { open, toggle });
</script>

<div class="menu">
    <slot />
</div>
