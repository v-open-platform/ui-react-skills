# Routing & Navigation

Routing and navigation in `@v-miniapp/ui-react` App framework.

---

## Navigation Hook

**When to use:** Programmatic navigation between pages.

**Import:** `import { useNavigate } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
import { useNavigate } from '@v-miniapp/ui-react'

function MyPage() {
  const navigate = useNavigate()

  const goToSettings = () => {
    navigate('/settings')
  }

  const goBack = () => {
    navigate(-1) // Go back 1 page
  }

  return <Button onClick={goToSettings}>Go to Settings</Button>
}
```

**Navigate to pathname:**

```tsx
navigate('/settings', {
  replace: false, // Use replace instead of push
  params: { id: '123' }, // URL params
  state: { data: 'value' }, // Page state
})
```

**Navigate by delta:**

```tsx
navigate(-1) // Go back
navigate(1) // Go forward
navigate(-2, { replace: true }) // Go back 2 pages with replace
```

---

## Link Component

**When to use:** Declarative navigation links.

**Import:** `import { Link } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
import { Link } from '@v-miniapp/ui-react'

function MyPage() {
  return <Link to="/settings">Go to Settings</Link>
}
```

**With params:**

```tsx
<Link to="/user" params={{ id: '123' }}>
  View User
</Link>
```

**With replace:**

```tsx
<Link to="/settings" replace>
  Settings
</Link>
```

**Navigate by delta:**

```tsx
<Link to={-1}>Go Back</Link>
<Link to={1}>Go Forward</Link>
```

---

## Page State & Params

**When to use:** Access route params and navigation state in pages.

**Import:** `import { useLocation, useHistory } from '@v-miniapp/ui-react'`

**Access search params (query params):**

```tsx
import { useLocation } from '@v-miniapp/ui-react'

function UserPage() {
  const location = useLocation()

  // Access search params from URL
  const userId = location?.params?.id
  const search = location?.params?.search

  return <div>User ID: {userId}</div>
}
```

**Alternative: Access via useHistory:**

```tsx
import { useHistory } from '@v-miniapp/ui-react'

function UserPage() {
  const history = useHistory()

  // Access search params from URL
  const userId = history?.location?.params?.id
  const search = history?.location?.params?.search

  return <div>User ID: {userId}</div>
}
```

**Access navigation state:**

```tsx
import { useLocation } from '@v-miniapp/ui-react'

function MyPage() {
  const location = useLocation()

  // Access state passed via navigate(..., { state: {...} })
  const navigationState = location?.state

  return <div>State: {JSON.stringify(navigationState)}</div>
}
```

---

## Navigation Options

**Pathname navigation:**

- `to`: `string` - Pathname to navigate to
- `replace?`: `boolean` - Replace current history entry
- `params?`: `Record<string, string>` - URL parameters
- `state?`: `any` - Page state (accessible via `usePageState()`)

**Delta navigation:**

- `to`: `number` - Number of pages to go back (negative) or forward (positive)
- `replace?`: `boolean` - Replace history entry

---

## Page Configuration

**Page-level navigation config:**

```tsx
const appConfig: IAppConfig = {
  pages: [
    {
      pathname: '/settings',
      Component: SettingsPage,
      navigationBar: {
        title: 'Settings',
        backIcon: true,
      },
      animation: {
        type: 'slide_left',
      },
      keepAlive: true, // Keep page state when navigating away
    },
  ],
}
```

**Page-level options:**

- `navigationBar`: Navigation bar config for this page
- `animation`: Page transition animation
- `keepAlive`: `boolean` - Keep page state
- `freeze`: `boolean` - Freeze page when inactive
- `Layouts`: Array of page-level layout components

---

## Important Notes

- **History stack:** App maintains navigation history. Use `navigate(-1)` to go back.
- **Keep-alive:** Pages with `keepAlive: true` preserve state when navigating away.
- **URL params:** Passed via `params` option in `navigate()` or `Link`, accessible via `useLocation()?.params` or `useHistory()?.location?.params`.
- **Navigation state:** Passed via `state` option in `navigate()`, accessible via `useLocation()?.state` or `useHistory()?.location?.state`.
- **Initial route:** First page in `pages` array is default, or match URL pathname.
