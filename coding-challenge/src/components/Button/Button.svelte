<script lang="ts">
    export let onClick = () => {};
    export let type: any = "button";
    export let disabled: boolean = false;
    /** When true, show 2px #B0B0B0 outline on focus/hover. Set false e.g. when dropdown is open. */
    export let showFocusStroke = true;

    const base = "w-full h-[40px] rounded-lg bg-white flex items-center justify-between px-4 hover:bg-gray-50 text-left cursor-pointer font-medium";
    const stroke = "focus:outline focus:outline-2 focus:outline-[#B0B0B0] focus:outline-offset-0 hover:outline hover:outline-2 hover:outline-[#B0B0B0] hover:outline-offset-0";
</script>

<button 
    type={type} 
    class="{base} {showFocusStroke ? stroke : ''}"
    disabled={disabled}
    on:click={onClick}>
    <slot />
</button>
