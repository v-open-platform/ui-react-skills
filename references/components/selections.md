# Selections Components

Selection controls: Radio, Checkbox, Chip, Switch, OptionItem.

---

## Radio

**When to use:** Single selection from a group.

**Import:** `import { Radio } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Radio
  checked={selected === 'option1'}
  onChange={checked => setSelected(checked ? 'option1' : null)}>
  Option 1
</Radio>
```

**Key props:**

- `checked`: `boolean`
- `onChange`: `(checked: boolean) => void`
- `theme`: `'brand' | 'neutral'`
- `type`: `'checkbox' | 'radio'` (default: `'radio'`)
- `disabled`: `boolean`
- `children`: Label content
- `typography`: Typography props for label
- `...props`: `ComponentProps<'input'>` - All standard HTML input element props are supported

---

## Checkbox

**When to use:** Multiple selection or single toggle.

**Import:** `import { Checkbox } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Checkbox checked={isChecked} onChange={checked => setIsChecked(checked)}>
  Accept terms
</Checkbox>
```

**Key props:**

- `checked` / `defaultChecked`: `boolean`
- `onChange`: `(checked: boolean) => void`
- `theme`: `'brand' | 'inverse'`
- `variant`: `'default' | 'number' | 'indeterminate'`
- `number`: Number badge (when `variant='number'`)
- `onNumberChange`: `(number: number | undefined) => void`
- `disabled`: `boolean`
- `children`: Label content
- `...props`: `ComponentProps<'input'>` - All standard HTML input element props are supported

---

## Chip

**When to use:** Tag/filter selection, action chips.

**Import:** `import { Chip } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Chip
  type="selection"
  selected={isSelected}
  label="Tag"
  leadingIcon={{ name: 'tag' }}
/>
```

**Key props:**

- `type`: `'selection' | 'dropdown' | 'action' | 'input'`
- `theme`: `'default' | 'brand' | 'neutral'`
- `selected`: `boolean`
- `label`: Label text or ReactNode
- `leadingIcon` / `trailingIcon`: Icon props
- `count`: Number badge
- `disabled`: `boolean`
- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div element props are supported

---

## Switch

**When to use:** Toggle on/off state.

**Import:** `import { Switch } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Switch checked={enabled} onChange={checked => setEnabled(checked)} />
```

**Key props:**

- `checked` / `defaultChecked`: `boolean`
- `onChange`: `(checked: boolean) => void`
- `theme`: `'brand' | 'inverse'`
- `disabled`: `boolean`
- `...props`: `ComponentProps<'input'>` - All standard HTML input element props are supported

---

## OptionItem

**When to use:** List item in dropdowns/sheets (used internally by Dropdown, but can be used standalone).

**Import:** `import { OptionItem } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<OptionItem
  selected={isSelected}
  onChange={selected => setIsSelected(selected)}
  theme="brand">
  Option text
</OptionItem>
```

**Key props:**

- `selected` / `defaultSelected`: `boolean`
- `onChange`: `(selected: boolean) => void`
- `theme`: `'brand' | 'neutral'`
- `divider`: `boolean` (show divider below, default: `true`)
- `...props`: `ComponentProps<'div'>` - All standard HTML div element props are supported
