<script lang="ts">
  import Menu from "./components/Menu/Menu.svelte"
  import MenuButton from "./components/Menu/MenuButton.svelte";
  import MenuDropdown from "./components/Menu/MenuDropdown.svelte";
  import MenuItem from "./components/Menu/MenuItem.svelte";
</script>

<!-- 40px from top of screen to button; centered horizontally -->
<main class="min-h-screen w-full flex justify-center items-start pt-10 bg-[#e5e5e5] px-4 pb-4 sm:px-6 sm:pb-6 box-border">
  <Menu>
    <MenuButton>
      <!-- Placeholder when nothing selected -->
      <span class="font-normal text-base text-gray-500">
        Select a product
      </span>
    </MenuButton>
    <MenuDropdown>
      <MenuItem value="Website">Website</MenuItem>
      <MenuItem value="Web App">Web App</MenuItem>
      <MenuItem value="Mobile App">Mobile App</MenuItem>
    </MenuDropdown>
  </Menu>
</main>

<style>

</style>
