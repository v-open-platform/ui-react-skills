# Modal Components

Overlay dialogs: Dialog, Sheet.

---

## Dialog

**When to use:** Modal dialog (centered, for confirmations, alerts, forms).

**Import:** `import { Dialog } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Dialog
  open={isOpen}
  title="Confirm"
  description="Are you sure?"
  footer={
    <>
      <Button onClick={handleCancel}>Cancel</Button>
      <Button onClick={handleConfirm}>Confirm</Button>
    </>
  }
  onBackdropClick={() => setIsOpen(false)}
  onCloseClick={() => setIsOpen(false)}
/>
```

**Key props:**

- `open`: `boolean` (control visibility)
- `title`: Title text or ReactNode
- `description`: Description text or ReactNode
- `topImageUrl`: Image URL at top
- `top`: Custom ReactNode at top
- `children`: Main content
- `footer`: Footer content (ReactNode, typically buttons)
- `closeAction`: `boolean` (show close button)
- `onCloseClick`: Close button handler
- `onBackdropClick`: Backdrop click handler
- `overlay`: `'default' | 'blur'` (overlay style)
- `portal`: `boolean` (render in portal, default: `true`)
- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div element props are supported

---

## Sheet

**When to use:** Bottom sheet (slides up from bottom, for actions, forms, lists).

**Import:** `import { Sheet, SheetHeader, SheetBody, SheetFooter } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Sheet open={isOpen} onBackdropClick={() => setIsOpen(false)}>
  <SheetHeader title="Title" />
  <SheetBody>Content here</SheetBody>
  <SheetFooter>
    <Button>Action</Button>
  </SheetFooter>
</Sheet>
```

**Key props:**

- `open`: `boolean` (control visibility)
- `onBackdropClick`: Backdrop click handler
- `overlay`: `'default' | 'blur'` (overlay style)
- `portal`: `boolean` (render in portal, default: `true`)

**Sub-components:**

- `SheetHeader`: Header with title (optional close button)
- `SheetBody`: Scrollable content area
- `SheetFooter`: Footer area (typically buttons)

**Note:** Sheet is used internally by Dropdown and DatePicker. Use standalone for custom bottom sheets.
