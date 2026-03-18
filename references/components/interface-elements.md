# Interface Elements Components

UI building blocks: Avatar, Carousel, Section.

---

## Avatar

**When to use:** User profile picture or initials.

**Import:** `import { Avatar } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Avatar src="/avatar.jpg" size={40} shape="circle" label="AB" />
```

**Key props:**

- `src`: Image URL
- `size`: Number (default: `40`)
- `shape`: `'circle' | 'rounded'` (default: `'rounded'`)
- `label`: String (fallback text if image fails)
- `border`: `boolean` (show border)
- `labelColor` / `labelSize`: Typography props for label
- `color`: Background color token (when no image)
- `...props`: `ComponentProps<'img'>` - All standard HTML img element props are supported (alt, loading, etc.)

---

## Carousel

**When to use:** Swipeable image/content carousel.

**Import:** `import { Carousel } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<Carousel pagination={true}>
  <div>Slide 1</div>
  <div>Slide 2</div>
  <div>Slide 3</div>
</Carousel>
```

**Key props:**

- `children`: ReactNode (carousel slides)
- `pagination`: `boolean` (show pagination dots, default: `true`)
- `carousel`: Carousel instance
- `options`: Carousel options (autoplay, loop, etc.)

**Additional props:**

- `className`: Custom CSS class
- Standard React props for children

---

## Section

**When to use:** Content section wrapper (layout helper).

**Import:** `import { SectionContent } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<SectionContent>Section content here</SectionContent>
```

**Key props:**

- `space`: `boolean` (add spacing, default: `true`)
- `shape`: `'rounded' | 'square'` (default: `'rounded'`)
- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div/section element props are supported

**Note:** Simple wrapper component for consistent section styling. Accepts standard div props.
