# App Setup

Basic setup for `App` component from `@v-miniapp/ui-react`.

---

## Basic Setup

**When to use:** Initialize the App component with pages, navigation, and app-level configuration.

**Import:** `import { App, type IAppConfig } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
import { App, type IAppConfig } from '@v-miniapp/ui-react'

const HomePage = () => <div>Home</div>
const SettingsPage = () => <div>Settings</div>

const appConfig: IAppConfig = {
  pages: [
    {
      pathname: '/',
      Component: HomePage,
    },
    {
      pathname: '/settings',
      Component: SettingsPage,
    },
  ],
}

export function MiniApp() {
  return <App config={appConfig} />
}
```

---

## App Config Structure

**Key properties:**

- `pages`: Array of page configurations

  - `pathname`: `string` - Route path
  - `Component`: React component for the page
  - `Layouts?`: Array of layout components
  - `bottomTabBarId?`: `string` - ID for bottom tab bar item
  - Page-level state (navigationBar, animation, keepAlive, etc.)

- `animation?`: App-level animation config

  - `type`: `'none' | 'slide_up' | 'slide_left' | 'fade_in'`

- `keepAlive?`: Keep-alive config (preserve page state)

  - `enable`: `boolean` - Enable keep-alive
  - `maxStack`: `number` - Maximum pages in stack
  - `freeze`: `boolean` - Freeze inactive pages
  - `freezeDelay`: `number` - Delay before freezing

- `navigationBar?`: Navigation bar config

  - `hidden`: `boolean` - Hide navigation bar
  - Other NavigationBar props (title, backIcon, etc.)

- `bottomTabBar?`: Bottom tab bar config

  - `items`: Array of tab items with `path`
  - `hidden`: `boolean` - Hide bottom tab bar

- `pageLayout?`: Page layout config

  - `hidden`: `boolean` - Hide page layout
  - `scrollRestoration`: `boolean` - Restore scroll position

- `darkMode?`: Dark mode config

  - `defaultEnabled`: `boolean` - Enable dark mode by default

- `Layouts?`: Array of app-level layout components

---

## App Config with Locales

**When to use:** Setup App with i18n support.

```tsx
import { App, type IAppConfig, type ILocalesConfig } from '@v-miniapp/ui-react'

const localesConfig: ILocalesConfig = {
  defaultLanguage: 'vi',
  resources: {
    vi: { 'app.title': 'Ứng dụng' },
    en: { 'app.title': 'Application' },
  },
}

const appConfig: IAppConfig = {
  pages: [
    /* ... */
  ],
}

export function MiniApp() {
  return <App config={appConfig} localesConfig={localesConfig} />
}
```

**Note:** App config can be a function that receives `{ t }` context for dynamic translations.

---

## Important Notes

- **App config is constant:** Config is initialized once and won't re-render on changes. Use state management for dynamic updates.
- **NavigationBar:** When using `App` component, NavigationBar is managed automatically. Set `window.defaultTitle: ""` and `window.transparentTitle: "always"` in `app-config.json` to hide native title bar.
- **Initial page:** First page in `pages` array is the initial page, or use URL pathname matching.
