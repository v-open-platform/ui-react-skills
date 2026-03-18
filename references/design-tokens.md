# Design Tokens

Design tokens exported from `@v-miniapp/ui-react` for consistent styling and theming.

---

## Color Tokens

**When to use:** Use design system color tokens instead of hardcoded color values.

**Import:** `import type { IColor, IThemeColor } from '@v-miniapp/ui-react'`

**Available tokens:**

Color tokens are available as CSS variables and can be used in:

- Component props (e.g., `color`, `bgColor` props)
- Tailwind CSS classes (when using Tailwind integration)
- CSS custom properties

### Token Categories

**Alias tokens** (semantic colors):

- `alias-layer-*` - Background layers
- `alias-text-*` - Text colors
- `alias-object-*` - Object colors (buttons, badges, etc.)
- `alias-border-*` - Border colors
- `alias-link-*` - Link colors
- `alias-support-*` - Support colors (info, warning, error, success)
- `alias-background-*` - Background colors
- `alias-custom-brand-*` - Custom brand colors

**Global tokens** (color palette):

- `global-{color}-{shade}` - Color palette tokens (e.g., `global-blue-blue-50`, `global-red-red-60`)
- Available colors: amber, blue, cyan, emerald, fuchsia, gray, green, indigo, lime, neutral, orange, pink, purple, red, rose, sky, slate, stone, teal, violet, yellow, zinc
- Shades: 05, 10, 20, 30, 40, 50, 60, 70, 80, 90, 95

### Usage in Components

```tsx
import { Button } from '@v-miniapp/ui-react'

// Use color tokens in component props
<Button color="alias-object-brand">Click me</Button>
<Button bgColor="alias-background-brand">Click me</Button>
```

### Usage in CSS

```css
/* Use CSS variables directly */
.my-element {
  background-color: var(--color-alias-layer-01);
  color: var(--color-alias-text-primary);
  border-color: var(--color-alias-border-subtle-01);
}
```

### Usage with Tailwind Integration

When using Tailwind integration (`@import '@v-miniapp/ui-react/tailwind'`), color tokens are available as Tailwind utilities:

```tsx
// Use color tokens in Tailwind classes
<div className="bg-alias-layer-01 text-alias-text-primary border-alias-border-subtle-01">
  Content
</div>
```

**Note:** Color tokens use the format `--color-{token-name}` as CSS variables. In Tailwind, they're available as `{token-name}` (without the `--color-` prefix).

---

## TypeScript Types

**Import:** `import type { IColor, IThemeColor } from '@v-miniapp/ui-react'`

**Types:**

- `IThemeColor`: Union type of all theme color token names
- `IColor`: `IThemeColor | string` - Accepts theme tokens or custom color strings

**Usage:**

```tsx
import type { IColor } from '@v-miniapp/ui-react'

const myColor: IColor = 'alias-object-brand' // Valid theme token
const customColor: IColor = '#ff0000' // Also accepts custom strings
```

---

## Tailwind Integration

**When to use:** Use Tailwind CSS with `@v-miniapp/ui-react` design tokens.

**Setup:**

1. Import Tailwind integration in your CSS file:

```css
/* tailwind.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

/* Import Tailwind integration from @v-miniapp/ui-react */
@import '@v-miniapp/ui-react/tailwind';
```

2. **Important:** When using Tailwind integration, **do NOT** import `@v-miniapp/ui-react/styles.css` anymore.

3. Use design tokens in Tailwind classes:

```tsx
<div className="bg-alias-layer-01 text-alias-text-primary p-4">
  Content with design tokens
</div>
```

### Available Tailwind Tokens

When using Tailwind integration, the following tokens are available:

**Colors:**

- All `alias-*` tokens (e.g., `bg-alias-layer-01`, `text-alias-text-primary`)
- All `global-*` tokens (e.g., `bg-global-blue-blue-50`, `text-global-red-red-60`)

**Note:** Tokens are exposed as CSS variables in the `@theme` directive, making them available to Tailwind's utility classes.

---

## Custom Theme Override

You can override design tokens by setting CSS variables:

```css
:root {
  /* Override a specific token */
  --color-alias-object-brand: #your-custom-color;

  /* Or override multiple tokens */
  --color-alias-layer-01: #ffffff;
  --color-alias-text-primary: #000000;
}
```

**Note:** Override tokens at the `:root` level to apply globally, or scope them to specific components/elements.

---

## Important Notes

- **Use tokens, not hardcoded values:** Always prefer design tokens over hardcoded color values for consistency
- **Type safety:** Use `IColor` type for component props that accept colors
- **Tailwind integration:** When using Tailwind, import `@v-miniapp/ui-react/tailwind` instead of `styles.css`
- **CSS variables:** All tokens are available as CSS variables with the `--color-` prefix
- **Token generation:** Color tokens are auto-generated from the design system SCSS files
