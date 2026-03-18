# Form Components

Input fields, labels, and form controls.

---

## Label

**When to use:** Field labels with optional required indicator, icon, helper text.

**Import:** `import { Label } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Label text="Email" required helperText="Enter your email" />
```

**Key props:**

- `text`: Label text
- `required`: `boolean` (shows asterisk)
- `icon`: Icon props or ReactNode
- `helperText`: Helper text below label
- `disabled`: `boolean`
- `loading`: `boolean`
- `...props`: `ComponentPropsWithRef<'label'>` - All standard HTML label element props are supported (htmlFor, etc.)

---

## TextField

**When to use:** Text input (single line).

**Import:** `import { TextField } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<TextField
  label="Name"
  placeholder="Enter name"
  value={value}
  onChange={val => setValue(val)}
/>
```

**Key props:**

- `label`: `ILabelProps` - Label configuration
- `value` / `defaultValue`: Controlled/uncontrolled value
- `onChange`: `(value: string) => void`
- `placeholder`: Placeholder text
- `shape`: `'rounded' | 'pill'` (default: `'rounded'`)
- `disabled`: `boolean` - Whether the input is disabled
- `error`: `boolean` - Whether the field has an error state
- `errorMessage`: `ReactNode` - Error message to display
- `success`: `boolean` - Whether the field has a success state
- `successMessage`: `ReactNode` - Success message to display
- `loading`: `boolean` - Loading state
- `leadingIcon`: `IIconProps | ReactNode` - Icon on the left side
- `onLeadingIconClick`: `(event: React.MouseEvent) => void` - Leading icon click handler
- `trailingIcon`: `IIconProps | ReactNode` - Icon on the right side
- `onTrailingIconClick`: `(event: React.MouseEvent) => void` - Trailing icon click handler
- `prefix`: `ReactNode` - Prefix content before input value
- `suffix`: `ReactNode` - Suffix content after input value
- `maxLength`: `number` - Maximum character length
- `loadingType`: `'search' | 'input'` - Loading skeleton type
- `inputClassName`: `string` - CSS class for input element
- `className`: `string` - CSS class for wrapper
- `...props`: `ComponentProps<'input'>` - All standard HTML input element props are supported

---

## NumberField

**When to use:** Numeric input with optional masking.

**Import:** `import { NumberField } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<NumberField
  label="Amount"
  value={value}
  onChange={val => setValue(val)}
  masked={false}
  length={10}
/>
```

**Key props:**

- `value` / `defaultValue`: `string` (numeric string)
- `onChange`: `(value: string) => void`
- `masked`: `boolean` (hide numbers, e.g. for PIN)
- `length`: Max length
- `label`: `ILabelProps` - Label configuration
- `shape`: `'rounded' | 'pill'` (default: `'rounded'`)
- `disabled`: `boolean` - Whether the input is disabled
- `error`: `boolean` - Whether the field has an error state
- `errorMessage`: `string` - Error message to display
- `success`: `boolean` - Whether the field has a success state
- `successMessage`: `ReactNode` - Success message to display
- `loading`: `boolean` - Loading state
- `leadingIcon`: `IIconProps | ReactNode` - Icon on the left side
- `onLeadingIconClick`: `(event: React.MouseEvent) => void` - Leading icon click handler
- `trailingIcon`: `IIconProps | ReactNode` - Icon on the right side
- `onTrailingIconClick`: `(event: React.MouseEvent) => void` - Trailing icon click handler
- `prefix`: `ReactNode` - Prefix content before input value
- `suffix`: `ReactNode` - Suffix content after input value
- `className`: `string` - CSS class for wrapper
- `...props`: `ComponentProps<'div'>` - All standard HTML div element props are supported

---

## DateField

**When to use:** Date input (single or range).

**Import:** `import { DateField } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<DateField label="Date" value={date} onChange={val => setDate(val)} />
```

**Key props:**

- `value`: `Date | null` - Selected date value
- `onChange`: `(value: Date | null) => void` - Date change handler
- `picker`: `boolean | IDatePickerSheetProps` - Picker configuration
- `label`: `ILabelProps` - Label configuration
- `shape`: `'rounded' | 'pill'` (default: `'rounded'`)
- `disabled`: `boolean` - Whether the field is disabled
- `error`: `boolean` - Whether the field has an error state
- `errorMessage`: `ReactNode` - Error message to display
- `success`: `boolean` - Whether the field has a success state
- `successMessage`: `ReactNode` - Success message to display
- `loading`: `boolean` - Loading state
- `leadingIcon`: `IIconProps | ReactNode` - Icon on the left side
- `onLeadingIconClick`: `(event: React.MouseEvent) => void` - Leading icon click handler
- `trailingIcon`: `IIconProps | ReactNode` - Icon on the right side
- `onTrailingIconClick`: `(event: React.MouseEvent) => void` - Trailing icon click handler
- `prefix`: `ReactNode` - Prefix content before input value
- `suffix`: `ReactNode` - Suffix content after input value
- `inputClassName`: `string` - CSS class for input element
- `className`: `string` - CSS class for wrapper
- `...props`: `ComponentProps<'input'>` - All standard HTML input element props are supported

---

## SearchField

**When to use:** Search input with magnifier icon.

**Import:** `import { SearchField } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<SearchField
  placeholder="Search..."
  value={query}
  onChange={val => setQuery(val)}
/>
```

**Key props:**

- Similar to TextField props (no `trailingIcon` / `onTrailingIconClick` - managed internally)
- `label`: `ILabelProps` - Label configuration
- `shape`: `'rounded' | 'pill'` (default: `'rounded'`)
- `disabled`: `boolean` - Whether the field is disabled
- `error`: `boolean` - Whether the field has an error state
- `errorMessage`: `ReactNode` - Error message to display
- `success`: `boolean` - Whether the field has a success state
- `successMessage`: `ReactNode` - Success message to display
- `loading`: `boolean` - Loading state
- `leadingIcon`: `IIconProps | ReactNode` - Icon on the left side (overrides default magnifier)
- `onLeadingIconClick`: `(event: React.MouseEvent) => void` - Leading icon click handler
- `prefix`: `ReactNode` - Prefix content before input value
- `suffix`: `ReactNode` - Suffix content after input value
- `clearable`: `boolean` - Show clear button when there's text (default: `true`)
- `onClear`: `() => void` - Clear button click handler
- `className`: `string` - CSS class for wrapper
- `...props`: `ComponentProps<'input'>` - All standard HTML input element props are supported

**Note:** Built on TextField with search icon. Props similar to TextField but `trailingIcon` and `onTrailingIconClick` are managed internally (clear button).

---

## TextArea

**When to use:** Multi-line text input.

**Import:** `import { TextArea } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<TextArea
  label="Description"
  value={text}
  onChange={val => setText(val)}
  rows={4}
/>
```

**Key props:**

- `value` / `defaultValue`: `string` - Textarea value
- `onChange`: `(value: string) => void` - Value change handler
- `label`: `ILabelProps` - Label configuration
- `shape`: `'rounded' | 'pill'` (default: `'rounded'`)
- `disabled`: `boolean` - Whether the textarea is disabled
- `error`: `boolean` - Whether the field has an error state
- `errorMessage`: `ReactNode` - Error message to display
- `success`: `boolean` - Whether the field has a success state
- `successMessage`: `ReactNode` - Success message to display
- `loading`: `boolean` - Loading state
- `leadingIcon`: `IIconProps | ReactNode` - Icon on the left side
- `onLeadingIconClick`: `(event: React.MouseEvent) => void` - Leading icon click handler
- `trailingIcon`: `IIconProps | ReactNode` - Icon on the right side
- `onTrailingIconClick`: `(event: React.MouseEvent) => void` - Trailing icon click handler
- `prefix`: `ReactNode` - Prefix content before textarea value
- `suffix`: `ReactNode` - Suffix content after textarea value
- `maxLength`: `number` - Maximum character length
- `autoHeight`: `boolean` - Auto-adjust height based on content
- `rows`: `number` - Initial number of rows (default: `3`)
- `inputClassName`: `string` - CSS class for textarea element
- `className`: `string` - CSS class for wrapper
- `...props`: `ComponentProps<'textarea'>` - All standard HTML textarea element props are supported

---

## Dropdown

**When to use:** Select from a list of options (opens in Sheet).

**Import:** `import { Dropdown } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Dropdown
  label="Choose option"
  options={[
    { value: '1', label: 'Option 1' },
    { value: '2', label: 'Option 2' },
  ]}
  value={selected}
  onChange={val => setSelected(val)}
/>
```

**Key props:**

- `options`: `IDropdownOption[]` - Array of options (required)
- `value`: Selected value
- `onChange`: `(value) => void` - Selection change handler
- `placeholder`: `string` - Placeholder text
- `label`: `ILabelProps` - Label configuration
- `shape`: `'rounded' | 'pill'` (default: `'rounded'`)
- `disabled`: `boolean` - Whether the dropdown is disabled
- `error`: `boolean` - Whether the field has an error state
- `errorMessage`: `ReactNode` - Error message to display
- `success`: `boolean` - Whether the field has a success state
- `successMessage`: `ReactNode` - Success message to display
- `loading`: `boolean` - Loading state
- `leadingIcon`: `IIconProps | ReactNode` - Icon on the left side
- `onLeadingIconClick`: `(event: React.MouseEvent) => void` - Leading icon click handler
- `trailingIcon`: `IIconProps | ReactNode` - Icon on the right side
- `onTrailingIconClick`: `(event: React.MouseEvent) => void` - Trailing icon click handler
- `prefix`: `ReactNode` - Prefix content before dropdown value
- `suffix`: `ReactNode` - Suffix content after dropdown value
- `allowSearch`: `boolean` - Enable search in dropdown sheet
- `searchFilter`: `(option, search) => boolean` - Custom search filter function
- `searchProps`: `ISearchFieldProps` - Props for search field
- `emptyText`: `ReactNode` - Text when no options match
- `renderLabel`: `(option, value) => ReactNode` - Custom label renderer
- `renderItem`: `(option, context) => ReactNode` - Custom item renderer
- `renderValue`: `(option) => ReactNode` - Custom value renderer
- `sheetTitle`: `ReactNode` - Sheet title
- `children`: `ReactNode` - Custom trigger element
- `className`: `string` - CSS class for wrapper
- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div element props are supported

---

## DatePicker

**When to use:** Date selection with calendar UI (opens in Sheet).

**Import:** `import { DatePicker } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<DatePicker label="Pick date" value={date} onChange={val => setDate(val)} />
```

**Key props:**

- `value`: Date string or range
- `onChange`: `(value) => void`
- `range`: `boolean` (date range)
- Standard field props
- `...props`: `ComponentProps<'div'>` - All standard HTML div element props are supported

---

## Calendar

**When to use:** Calendar component for date selection (single date or date range). Can be used standalone or in DatePicker.

**Import:** `import { Calendar } from '@v-miniapp/ui-react'`

**Basic usage (single date):**

```tsx
<Calendar
  type="single"
  value={selectedDate}
  onChange={date => setSelectedDate(date)}
/>
```

**Basic usage (date range):**

```tsx
<Calendar
  type="range"
  value={[startDate, endDate]}
  onChange={range => {
    setStartDate(range[0])
    setEndDate(range[1])
  }}
/>
```

**Key props:**

- `type`: `'single' | 'range'` (default: `'single'`)
- `value`: `Date | null` (single) or `[Date | null, Date | null]` (range)
- `defaultValue`: Same as `value` (uncontrolled)
- `onChange`: `(date: Date) => void` (single) or `(range: [Date | null, Date | null]) => void` (range)
- `minDate`: `Date` (minimum selectable date, default: `1900-01-01`)
- `maxDate`: `Date` (maximum selectable date, default: `2099-12-31`)
- `navigationMode`: `'month' | 'month-year' | 'time-only'` (navigation style)
- `lang`: `'vi' | 'en'` (language, uses app locale if not provided)
- `renderText`: Custom render functions for date, header, weekday labels
  - `date?: (date: Date) => ReactNode | ReactNode`
  - `dateSubText?: (date: Date) => ReactNode | ReactNode`
  - `headerLabel?: (month: IMonth, year: number) => ReactNode | ReactNode`
  - `weekday?: (weekday: IWeekday) => ReactNode | ReactNode`

**Range picker specific:**

- `onPick`: `(range: [Date | null, Date | null]) => void` (called when user picks a date, before range is complete)

**Additional props:**

- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div element props are supported

**Note:** Calendar supports both controlled and uncontrolled modes. For range picker, user selects start date first, then end date. Dates outside `minDate`/`maxDate` are disabled.

---

## Uploader

**When to use:** File/image upload with preview.

**Import:** `import { Uploader } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Uploader
  limit={5}
  value={files}
  onChange={files => setFiles(files)}
  showPreview={true}
/>
```

**Key props:**

- `value`: Array of `IFileUpload[]`
- `onChange`: `(files: IFileUpload[]) => void`
- `limit`: Max number of files
- `showPreview`: `boolean` (show image previews)
- `includeBase64`: `boolean` (include base64 in file data)
- `disabled`: `boolean`
- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div element props are supported

---

## Rating

**When to use:** Star rating input/display.

**Import:** `import { Rating } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Rating value={rating} onChange={val => setRating(val)} max={5} />
```

**Key props:**

- `value`: Number (0 to max)
- `onChange`: `(value: number) => void`
- `max`: Number of stars (default: 5)
- `readOnly`: `boolean`
- `size`: `'small' | 'medium' | 'large'`
- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div element props are supported
