# 🎯 Coding Challenge

A Svelte + TypeScript + Vite app featuring an accessible product selector menu. The dropdown uses the ARIA listbox/combobox pattern with keyboard navigation, type-ahead, and focus management. Built with composable Menu components and Tailwind CSS. Component documentation and isolated development are provided via Storybook.

## ✨ Features

- **Product selector menu** — Click to open a dropdown and choose an option (e.g. Website, Web App, Mobile App)
- **Accessible UI** — ARIA listbox/combobox, `aria-activedescendant`, screen-reader friendly labels, and focus return on close
- **Keyboard support** — Arrow keys to move, Enter/Space to select, Escape to close, type-ahead by first letter
- **Reusable components** — `Menu`, `MenuButton`, `MenuDropdown`, and `MenuItem` composed via Svelte context and slots
- **Storybook** — Component stories for Button and Menu, autodocs, and a11y testing
- **Simple, responsive layout** — Centered trigger, 250×132 dropdown, styled with Tailwind CSS
- **Vite-powered dev** — Fast HMR and TypeScript

## 🚀 Getting Started

Install dependencies:

```
npm install
```

Run the dev server:

```
npm run dev
```

Run Storybook for component docs and isolated UI development (optional):

```
npm run storybook
```

Build for production:

```
npm run build
```

Preview the production build:

```
npm run preview
```

Type-check (optional):

```
npm run check
```

## 📚 Storybook

Component documentation and isolated development with [Storybook](https://storybook.js.org/).

Run Storybook (dev server on port 6006):

```
npm run storybook
```

Build static Storybook for deployment:

```
npm run build-storybook
```

- **Component stories** — `Button` and `Menu` stories live next to their components in `src/components/Button/` and `src/components/Menu/`.
- **Example docs** — Intro and docs examples are in `src/components/_stories_examples/` (safe to remove when not needed).
- **Addons** — Includes docs, a11y (accessibility), and Vitest for component testing.

## 🗂️ Project Structure

- `src/App.svelte` — Main app; composes Menu with placeholder and product options
- `src/main.ts` — Svelte entry point; mounts App and loads global CSS
- `src/app.css` — Global styles and Tailwind
- `src/components/Menu/Menu.svelte` — Root: shared state (open, selected, options), context, keyboard handler, open/close/select logic
- `src/components/Menu/MenuButton.svelte` — Trigger; shows selected value or placeholder, ARIA combobox
- `src/components/Menu/MenuDropdown.svelte` — Listbox panel; shown when open, receives focus, ARIA listbox
- `src/components/Menu/MenuItem.svelte` — Single option; registers with Menu, click/Enter to select, checkmark when selected
- `src/components/Button/Button.svelte` — Reusable button with focus stroke and optional autofocus
- `src/components/Button/Button.stories.svelte` — Storybook stories for Button
- `src/components/Menu/*.stories.svelte` — Storybook stories for Menu
- `src/components/_stories_examples/` — Example docs and stories (optional; can be removed)
- `vite.config.ts` — Vite + Svelte + Tailwind configuration
- `.storybook/` — Storybook config (main, preview, addons)
- `index.html` — HTML shell and app mount point

## 🎮 Using the Menu

In the app (or in Storybook under **Components → Menu**):

1. Click the **Select a product** button to open the dropdown.
2. Use **Arrow Up/Down** to move focus, **Enter** or **Space** to select, **Escape** to close.
3. Type a letter to jump to the next option starting with that letter (type-ahead).
4. Click an option to select it; the button shows the selected value and a checkmark appears next to it.

## 🛠️ Customization

- Change options by editing the `MenuItem` list in `App.svelte` (e.g. add/remove or rename values).
- Adjust placeholder text in the `MenuButton` slot in `App.svelte`.
- Tweak dropdown size, spacing, or colors in `Menu.svelte`, `MenuDropdown.svelte`, and `MenuItem.svelte` (Tailwind classes).
- Modify focus ring and button styles in `Button.svelte` and `app.css`.
- Try component variants and states in Storybook (Button sizes/variants, Menu open/focused/selected).

## 🧰 Tech Stack

- **Svelte 5** — Components, reactivity, context, slots
- **TypeScript** — Typed props and context
- **Vite 7** — Dev server and build
- **Tailwind CSS 4** — Styling (`@tailwindcss/vite`)
- **Storybook 10** — Component docs, a11y addon, Vitest integration
- **lucide-svelte** — Icons (ChevronsUpDown, Check)

## 🙌 Recommended IDE

[VS Code](https://code.visualstudio.com/) with the [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode) extension for the best experience.
