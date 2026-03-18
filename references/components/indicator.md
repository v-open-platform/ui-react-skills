# Indicator Components

Status indicators: Badge.

---

## Badge

**When to use:** Small indicator for counts, status, notifications (typically on icons/buttons).

**Import:** `import { Badge, BadgeContainer } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<BadgeContainer>
  <Icon name="bell" />
  <Badge>5</Badge>
</BadgeContainer>
```

**Dot badge (no content):**

```tsx
<BadgeContainer>
  <Icon name="bell" />
  <Badge /> {/* Shows as dot */}
</BadgeContainer>
```

**Key props:**

- `outline`: `boolean` (outline style)
- `children`: Number or text (if empty, shows as dot)
- `...props`: `ComponentProps<'div'>` - All standard HTML div element props are supported

**BadgeContainer:**

- Wrapper component for positioning badge relative to another element
- Use to position badge on top-right of icon/button

**Common patterns:**

- Notification count: `<Badge>5</Badge>`
- Status dot: `<Badge />` (no children)
- Outline style: `<Badge outline>New</Badge>`
