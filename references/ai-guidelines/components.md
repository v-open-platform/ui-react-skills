# Component Guidelines

Critical guidelines for AI assistants when working with UI components in V-MiniApp projects.

---

## UI Component Usage Guidelines

**CRITICAL:** When adding or modifying UI elements in a V-MiniApp, **ALWAYS** use components from `@v-miniapp/ui-react` instead of native HTML elements or custom styled components.

### Component Priority Rules

1. **Always prefer @v-miniapp/ui-react components** over native HTML elements:

   - Use `Button` instead of `<button>` or styled buttons
   - Use `Typography` instead of `<h1>`, `<h2>`, `<p>`, etc.
   - Use `TextField`, `NumberField` (for OTP input with shape prop), `TextArea` instead of `<input>`, `<textarea>`
   - Use `Icon` instead of SVG icons or icon fonts
   - Use `Dialog`, `Sheet` instead of custom modals
   - Use `Toast`, `Alert`, `Tooltip` for feedback instead of custom notifications
   - Use `Avatar`, `Carousel`, `Section` for interface elements
   - Use `Radio`, `Checkbox`, `Switch`, `Chip` for selections
   - Use `NavigationBar`, `BottomTabBar`, `TabBar` for navigation

2. **Before creating custom UI**, check if a component exists in `@v-miniapp/ui-react`:

   - Review component references in `references/components/` directory
   - Check available components: Foundation, Actions, Form, Selections, Navigation, Interface Elements, Feedback, Modal, Indicator
   - Use the appropriate component from the library

3. **Import pattern:**

   ```tsx
   import { Button, Typography, Icon, TextField } from '@v-miniapp/ui-react'
   ```

4. **When to use native HTML:**

   - Only when no equivalent component exists in `@v-miniapp/ui-react`
   - For structural elements like `<div>`, `<section>` (but prefer `Section` component when appropriate)
   - For semantic HTML that doesn't have a UI component equivalent

5. **Styling:**
   - Components from `@v-miniapp/ui-react` follow the design system
   - Use component props for styling (size, theme, color, etc.)
   - Avoid inline styles or custom CSS when component props can achieve the same result
   - Import styles: `import '@v-miniapp/ui-react/styles.css'` (or Tailwind import if using Tailwind)

---

## Component Usage Examples

**Do not use native HTML:**

```tsx
// Bad: Using native button
<button onClick={handleClick}>Click me</button>

// Bad: Using native headings
<h1>Title</h1>
<p>Text content</p>

// Bad: Using native input
<input type="text" placeholder="Enter text" />
```

**Use @v-miniapp/ui-react components:**

```tsx
// Good: Using Button component
<Button type="solid" theme="brand" onClick={handleClick}>
  Click me
</Button>

// Good: Using Typography component
<Typography size="x-large" weight="bold">Title</Typography>
<Typography>Text content</Typography>

// Good: Using TextField component
<TextField placeholder="Enter text" />
```

---

## Verify Props After Code Generation

**CRITICAL:** After generating code, always verify that component props are correct and complete by checking the component references.

**Verification checklist:**

1. **Check prop values:**

   - Verify all prop values match the valid options from component documentation
   - Check component references in `references/components/` directory
   - Ensure prop names and values are spelled correctly (case-sensitive)

2. **Verify component usage:**

   - Confirm you're using the correct component from `@v-miniapp/ui-react`
   - Check that you're not accidentally using native HTML elements instead of components
   - Verify imports are correct

3. **Icon names:**
   - Verify icon names match exactly with the list in [Icon Names](../components/icon-names.md)
   - Icon names are lowercase kebab-case (e.g., `'home'`, `'home-outline'`, `'home-fill'`)

**Remember:** Always cross-reference generated code with component documentation to ensure props are valid and complete. When in doubt, check the component references or use TypeScript autocomplete to see valid values.

---

## Component Reference Quick Lookup

When implementing UI features, check these component groups first:

- **Foundation:** `Typography`, `Icon` - For text and icons
- **Actions:** `Button` - For clickable actions
- **Form:** `TextField` (use with `type="number"` for numeric input), `TextArea`, `DateField`, `Dropdown`, `SearchField`, `DatePicker`, `Uploader`, `Calendar`, `Rating`, `Label` - For form inputs
  - **Note:** `NumberField` is ONLY for OTP/PIN input. Use `TextField` with `type="number"` for all other numeric inputs.
- **Selections:** `Radio`, `Checkbox`, `Chip`, `Switch`, `OptionItem` - For selection controls
- **Navigation:** `NavigationBar`, `BottomTabBar`, `TabBar` - For navigation UI
- **Interface Elements:** `Avatar`, `Carousel`, `Section` - For content display
- **Feedback:** `Toast`, `Alert`, `Tooltip` - For user feedback
- **Modal:** `Dialog`, `Sheet` - For modal dialogs
- **Indicator:** `Badge` - For status indicators

See [Components References](../components/) for detailed usage of each component group.
