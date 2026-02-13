<script lang="ts">
    import { setContext }  from "svelte";
    import { writable, type Writable } from "svelte/store";

    const open: Writable<boolean> = writable(false);
    const selectedLabel: Writable<string | null> = writable(null);

    function toggle() {
        open.update(v => !v);
    }

    function close() {
        open.set(false);
    }

    function select(label: string) {
        selectedLabel.set(label);
        close();
    }

    setContext("menu", { open, toggle, close, select, selectedLabel });
</script>

<div class="menu relative w-[250px]">
    <slot />
</div>
