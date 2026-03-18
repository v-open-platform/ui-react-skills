# Feedback Components

User feedback: Toast, Alert, Tooltip.

---

## Toast

**When to use:** Temporary notification (auto-dismiss, appears at top/bottom).

**Import:** `import { Toast } from '@v-miniapp/ui-react'`

**Basic usage (imperative):**

```tsx
// Show toast
Toast.show({
  type: 'positive',
  message: 'Success!',
  action: 'Undo',
  onActionClick: () => {},
})

// Hide toast
Toast.hide()
```

**Basic usage (declarative):**

```tsx
<Toast
  type="informative"
  message="Info message"
  action="Action"
  onActionClick={handleAction}
/>
```

**Key props:**

- `type`: `'neutral' | 'informative' | 'positive' | 'negative'`
- `message`: Message text or ReactNode
- `action`: Action button text
- `onActionClick`: Action handler
- `closeAction`: `boolean` (show close button, default: `true`)
- `onCloseActionClick`: Close handler
- `icon`: Custom icon props or ReactNode
- `...props`: `ComponentProps<'div'>` - All standard HTML div element props are supported

**Note:** Prefer `Toast.show()` for programmatic toasts. Toast component is also available for declarative use.

---

## Alert

**When to use:** Inline alert message (persistent, in page content).

**Import:** `import { Alert } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Alert
  type="negative"
  title="Error"
  message="Something went wrong"
  closeable={true}
  action={<Button>Retry</Button>}
/>
```

**Key props:**

- `type`: `'informative' | 'positive' | 'negative'`
- `title`: Title text or ReactNode
- `message`: Message text or ReactNode
- `closeable`: `boolean | IIconProps | ReactNode` (show close button)
- `action`: Action button/element (ReactNode)
- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div element props are supported

---

## Tooltip

**When to use:** Contextual help text on hover/focus.

**Import:** `import { Tooltip } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Tooltip position="top" type="default">
  <Button>Hover me</Button>
  <div>Tooltip content</div>
</Tooltip>
```

**Key props:**

- `position`: `'top' | 'bottom' | 'left' | 'right' | 'top-left' | 'top-right' | 'bottom-left' | 'bottom-right' | 'left-top' | 'left-bottom' | 'right-top' | 'right-bottom'` (default: `'top'`)
- `type`: `'default' | 'reverse'`
- `closeable`: `boolean` (show close button)
- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div element props are supported

**Note:** Tooltip wraps a trigger element and shows tooltip content on hover/focus.
