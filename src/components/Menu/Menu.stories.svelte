<script module>
  import { defineMeta } from '@storybook/addon-svelte-csf';
  import Menu from './Menu.svelte';
  import MenuButton from './MenuButton.svelte';
  import MenuDropdown from './MenuDropdown.svelte';
  import MenuItem from './MenuItem.svelte';

  const { Story } = defineMeta({
    title: 'Components/Menu',
    component: Menu,
    tags: ['autodocs'],
  });
</script>

<Story name="Default" asChild>
  <Menu>
    <MenuButton>
      <span class="font-normal text-base text-gray-500">Select a product</span>
    </MenuButton>
    <MenuDropdown>
      <MenuItem value="Website">Website</MenuItem>
      <MenuItem value="Web App">Web App</MenuItem>
      <MenuItem value="Mobile App">Mobile App</MenuItem>
    </MenuDropdown>
  </Menu>
</Story>

<Story name="Focused" asChild>
  <Menu>
    <MenuButton autofocus>
      <span class="font-normal text-base text-gray-500">Select a product</span>
    </MenuButton>
    <MenuDropdown>
      <MenuItem value="Website">Website</MenuItem>
      <MenuItem value="Web App">Web App</MenuItem>
      <MenuItem value="Mobile App">Mobile App</MenuItem>
    </MenuDropdown>
  </Menu>
</Story>

<Story name="Open and hovered" asChild>
  <Menu initialOpen={true}>
    <MenuButton>
      <span class="font-normal text-base text-gray-500">Select a product</span>
    </MenuButton>
    <MenuDropdown>
      <MenuItem value="Website">Website</MenuItem>
      <MenuItem value="Web App">Web App</MenuItem>
      <MenuItem value="Mobile App">Mobile App</MenuItem>
    </MenuDropdown>
  </Menu>
</Story>

<Story name="After selection" asChild>
  <Menu initialSelected="Web App">
    <MenuButton>
      <span class="font-normal text-base text-gray-500">Select a product</span>
    </MenuButton>
    <MenuDropdown>
      <MenuItem value="Website">Website</MenuItem>
      <MenuItem value="Web App">Web App</MenuItem>
      <MenuItem value="Mobile App">Mobile App</MenuItem>
    </MenuDropdown>
  </Menu>
</Story>

<Story name="Open after selection" asChild>
  <Menu initialOpen={true} initialSelected="Web App">
    <MenuButton>
      <span class="font-normal text-base text-gray-500">Select a product</span>
    </MenuButton>
    <MenuDropdown>
      <MenuItem value="Website">Website</MenuItem>
      <MenuItem value="Web App">Web App</MenuItem>
      <MenuItem value="Mobile App">Mobile App</MenuItem>
    </MenuDropdown>
  </Menu>
</Story>
