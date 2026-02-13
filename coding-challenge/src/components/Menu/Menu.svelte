<script lang="ts">
    import { setContext } from "svelte";
    import { writable, type Writable } from "svelte/store";

    const open: Writable<boolean> = writable(false);
    const selectedLabel: Writable<string | null> = writable(null);
    const options: Writable<string[]> = writable([]);
    const focusedIndex: Writable<number> = writable(0);
    const buttonEl: Writable<HTMLButtonElement | null> = writable(null);

    const menuId = "menu-" + Math.random().toString(36).slice(2, 9);
    const listboxId = menuId + "-listbox";
    const buttonId = menuId + "-button";

    /** Synced when dropdown opens; MenuItems push in order so indices are stable. */
    let optionsList: string[] = [];
    let justOpened = false;

    function setButtonEl(el: HTMLButtonElement | null) {
        buttonEl.set(el);
    }

    function toggle() {
        if (!$open) {
            optionsList = [];
            options.set([]);
            focusedIndex.set(0);
            justOpened = true;
        }
        open.update((v) => !v);
    }

    $: if ($open && $options.length > 0 && justOpened) {
        justOpened = false;
        const i = $selectedLabel != null ? $options.indexOf($selectedLabel) : -1;
        focusedIndex.set(i >= 0 ? i : 0);
    }

    function close() {
        open.set(false);
        setTimeout(() => $buttonEl?.focus(), 0);
    }

    function select(label: string) {
        selectedLabel.set(label);
        close();
    }

    function registerOption(value: string): { id: string; index: number } {
        const index = optionsList.length;
        optionsList.push(value);
        options.set([...optionsList]);
        return { id: listboxId + "-option-" + index, index };
    }

    function selectByIndex(i: number) {
        const opts = $options;
        if (i >= 0 && i < opts.length) select(opts[i]);
    }

    function handleListboxKeydown(e: KeyboardEvent) {
        const opts = $options;
        const len = opts.length;
        if (len === 0) return;
        if (e.key === "Escape") {
            e.preventDefault();
            close();
            return;
        }
        if (e.key === "ArrowDown") {
            e.preventDefault();
            focusedIndex.update((i) => (i + 1) % len);
            return;
        }
        if (e.key === "ArrowUp") {
            e.preventDefault();
            focusedIndex.update((i) => (i - 1 + len) % len);
            return;
        }
        if (e.key === "Enter" || e.key === " ") {
            e.preventDefault();
            selectByIndex($focusedIndex);
        }
    }

    setContext("menu", {
        open,
        toggle,
        close,
        select,
        selectedLabel,
        listboxId,
        buttonId,
        options,
        focusedIndex,
        registerOption,
        selectByIndex,
        handleListboxKeydown,
        setButtonEl,
    });
</script>

<div class="menu relative w-[250px]">
    <slot />
</div>
