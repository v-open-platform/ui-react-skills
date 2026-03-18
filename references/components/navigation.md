# Navigation Components

Navigation elements: BottomTabBar, TabBar, NavigationBar.

---

## BottomTabBar

**When to use:** Bottom tab navigation (fixed at bottom, typically 3-5 tabs).

**Import:** `import { BottomTabBar } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<BottomTabBar
  items={[
    { id: 'home', name: 'Home', icon: { name: 'home' } },
    { id: 'profile', name: 'Profile', icon: { name: 'user' } },
  ]}
  activeId={activeTab}
  onItemClick={item => setActiveTab(item.id)}
/>
```

**Key props:**

- `items`: Array of `{ id: string, name: string, icon?: IIconProps | ReactNode, activeIcon?: IIconProps | ReactNode }`
- `activeId`: Currently active tab ID
- `onItemClick`: `(item, index) => void`
- `indicator`: `boolean` (show active indicator, default: `true`)
- `safeAreaBottomOffset`: `boolean` (respect safe area, default: `true`)
- `bgColor` / `color` / `activeColor`: Color tokens
- `...props`: `ComponentProps<'div'>` - All standard HTML div element props are supported

---

## TabBar

**When to use:** Horizontal tab bar (top navigation, scrollable tabs).

**Import:** `import { TabBar } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<TabBar
  items={[
    { id: 'tab1', name: 'Tab 1' },
    { id: 'tab2', name: 'Tab 2' },
  ]}
  activeId={activeTab}
  onItemClick={item => setActiveTab(item.id)}
/>
```

**Key props:**

- `items`: Array of `{ id: string, name?: ReactNode, icon?: IIconProps | ReactNode, badge?: IBadgeProps | boolean }`
- `activeId`: Currently active tab ID
- `onItemClick`: `(item, index) => void`
- `theme`: `'default' | 'brand' | 'neutral'`
- `scrollable`: `boolean` (scrollable tabs)
- `centered`: `boolean` (center tabs)
- `...props`: `ComponentPropsWithRef<'div'>` - All standard HTML div element props are supported

---

## NavigationBar

**When to use:** Top navigation bar with title, back button, actions (used by `App` component, can be standalone).

**Import:** `import { NavigationBar } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
<NavigationBar
  title="Page Title"
  backIcon={true}
  onBackClick={() => navigate(-1)}
  rightIcon={{ name: 'more' }}
  onRightIconClick={handleMore}
/>
```

**Key props:**

- `title`: Title text or ReactNode
- `backIcon`: `boolean | IIconProps | ReactNode` (show back button)
- `onBackClick`: Back button handler
- `leftIcon` / `rightIcon`: Icon props or ReactNode
- `onLeftIconClick` / `onRightIconClick`: Icon click handlers
- `left` / `right`: Custom ReactNode for left/right slots
- `transparent`: `'auto' | 'always' | 'none'` (transparent on scroll)
- `theme`: `'default' | 'inverse'`
- `divider`: `boolean` (show bottom divider)
- `scrollElementSelector`: Element or selector for scroll detection

**Note:** When using `App` from `@v-miniapp/ui-react`, NavigationBar is managed automatically. Use standalone NavigationBar for custom layouts.
