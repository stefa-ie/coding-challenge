<script lang="ts">
    export let onClick = () => {};
    export let type: any = "button";
    export let disabled: boolean = false;

    const base = "w-[250px] h-[40px] rounded-lg bg-gray-100 flex items-center justify-between px-4"
</script>

<button 
    type={type} 
    class={base}
    disabled={disabled}
    on:click={onClick}>
    <slot />
</button>
