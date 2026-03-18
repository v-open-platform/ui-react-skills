# Foundation Components

Basic building blocks: Typography and Icon.

---

## Typography

**When to use:** Text rendering with consistent sizing, weight, and color tokens.

**Import:** `import { Typography } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Typography size="large" weight="semibold" color="text-primary">
  Text content
</Typography>
```

**Key props:**

- `size`: `'inherit' | '5x-large' | '4x-large' | '3x-large' | '2x-large' | 'x-large' | 'large' | 'base' | 'small' | 'x-small' | '2x-small' | '3x-small'`
- `weight`: `'inherit' | 'bold' | 'semibold' | 'medium' | 'regular' | 'light' | '100'-'900'`
- `color`: Color token (e.g. `'text-primary'`, `'text-secondary'`)
- `component`: HTML element or component (default: `'p'`)
- `...props`: `ComponentPropsWithRef<ElementType>` - All standard HTML element props are supported based on the `component` prop

**Note:** Use Typography for all text to maintain design system consistency.

---

## Icon

**When to use:** Display icons from the icon set.

**Import:** `import { Icon } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Icon name="home" size={24} color="text-primary" />
```

**Key props:**

- `name`: Icon name (e.g. `'home'`, `'user'`, `'arrow-right'`). Use `-outline` or `-fill` suffix for variants.
- `size`: Number or string (default: `24`)
- `color`: Color token
- `animation`: `'spin' | 'ping' | 'pulse' | 'bounce'` (optional)
- `...props`: `Omit<ComponentProps<'svg'>, 'name' | 'type' | 'children'>` - Additional SVG element props (title, titleId, desc, descId, etc.)

**Note:** Icon names are TypeScript-typed. Check available icons via `iconNames` export or Storybook. See [Icon Names](icon-names.md) for complete list of all available icons.
