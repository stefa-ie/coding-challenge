<script module>
  import { defineMeta } from '@storybook/addon-svelte-csf';
  import Button from './Button.svelte';
  import { fn } from 'storybook/test';

  const onClick = fn();
  const { Story } = defineMeta({
    title: 'Components/Button',
    component: Button,
    tags: ['autodocs'],
    argTypes: {
      label: { control: 'text' },
      disabled: { control: 'boolean' },
      showFocusStroke: { control: 'boolean' },
      autofocus: { control: 'boolean' },
      variant: {
        control: { type: 'select' },
        options: ['primary', 'secondary'],
      },
      size: {
        control: { type: 'select' },
        options: ['small', 'middle', 'large'],
      },
    },
    args: {
      onClick,
      label: 'Button',
    }
  });

  const args = { onClick, label: 'Button' };
</script>

<Story name="Default" args={{ label: 'Button' }}>
  <Button {...args} label={args.label} />
</Story>


<Story name="Disabled" args={{ disabled: true, label: 'Disabled' }}>
  <Button {...args} disabled label="Disabled" />
</Story>

<Story name="Focused" args={{ autofocus: true, label: 'Focused on load' }}>
  <Button {...args} autofocus label="Focused on load" />
</Story>

<Story name="No focus stroke" args={{ showFocusStroke: false, label: 'No focus ring' }}>
  <Button {...args} showFocusStroke={false} label="No focus ring" />
</Story>

<Story name="With placeholder label" args={{ label: 'Select a product' }}>
  <Button {...args} label="Select a product" />
</Story>

<Story name="Primary" args={{ variant: 'primary', label: 'Primary' }}>
  <Button {...args} variant="primary" label="Primary" />
</Story>

<Story name="Secondary" args={{ variant: 'secondary', label: 'Secondary' }}>
  <Button {...args} variant="secondary" label="Secondary" />
</Story>

<Story name="Small" args={{ size: 'small', label: 'Small' }}>
  <Button {...args} size="small" label="Small" />
</Story>

<Story name="Middle" args={{ size: 'middle', label: 'Middle' }}>
  <Button {...args} size="middle" label="Middle" />
</Story>

<Story name="Large" args={{ size: 'large', label: 'Large' }}>
  <Button {...args} size="large" label="Large" />
</Story>
