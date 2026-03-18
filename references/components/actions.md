# Actions Components

User actions: Button.

---

## Button

**When to use:** Primary action trigger (submit, navigate, confirm).

**Import:** `import { Button } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Button type="solid" theme="brand" size="large" onClick={handleClick}>
  Click me
</Button>
```

**Key props:**

- `type`: `'solid' | 'solid-subtle' | 'outline' | 'ghost'`
- `theme`: `'default' | 'brand' | 'neutral' | 'neutral-inverse'`
- `size`: `'large' | 'medium'`
- `shape`: `'rounded' | 'pill'`
- `disabled`: `boolean`
- `loading`: `boolean` (shows spinner)
- `leadingIcon` / `trailingIcon`: Icon props or ReactNode
- `block`: `boolean` (full width)
- `htmlType`: `'button' | 'submit' | 'reset'`
- `...props`: `ComponentPropsWithRef<'button'>` - All standard HTML button element props are supported (onClick, etc.)

**Common patterns:**

- Primary action: `type="solid" theme="brand"`
- Secondary: `type="outline"` or `type="ghost"`
- Loading state: set `loading={true}`
- With icon: `leadingIcon={{ name: 'arrow-right' }}`
