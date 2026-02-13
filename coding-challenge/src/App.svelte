<script lang="ts">
  import Menu from "./components/Menu/menu.svelte";
  import MenuButton from "./components/Menu/MenuButton.svelte";
  import MenuDropdown from "./components/Menu/MenuDropdown.svelte";
  import MenuItem from "./components/Menu/MenuItem.svelte";
</script>

<main>
  <Menu>
    
  </Menu>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
