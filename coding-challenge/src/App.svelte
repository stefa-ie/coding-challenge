<script lang="ts">
  import Menu from "./components/Menu/Menu.svelte"
  import MenuButton from "./components/Menu/MenuButton.svelte";
  import MenuDropdown from "./components/Menu/MenuDropdown.svelte";
  import MenuItem from "./components/Menu/MenuItem.svelte";
</script>

<main>
  <Menu>
    <MenuButton>
      <span class="font-['Inter'] font-normal text-base text-gray-500">
        Select a product
      </span>
    </MenuButton>
  </Menu>
</main>

<style>

</style>
