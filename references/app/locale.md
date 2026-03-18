# Locale (i18n)

Internationalization and localization in `@v-miniapp/ui-react`.

---

## Basic Setup

**When to use:** Add multi-language support to your app.

**Import:** `import { App, type ILocalesConfig } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
import { App, type ILocalesConfig } from '@v-miniapp/ui-react'

const localesConfig: ILocalesConfig = {
  defaultLanguage: 'vi',
  resources: {
    vi: {
      'app.title': 'Ứng dụng',
      'user.greeting': 'Xin chào {name}!',
    },
    en: {
      'app.title': 'Application',
      'user.greeting': 'Hello {name}!',
    },
  },
}

export function MiniApp() {
  return <App config={appConfig} localesConfig={localesConfig} />
}
```

**Language priority:**

1. `defaultLanguage` from config
2. `langCode` from URL search params (`?langCode=en`)
3. Default: `'vi'`

---

## Translation Hook

**When to use:** Translate text in components.

**Import:** `import { useTranslate } from '@v-miniapp/ui-react'`

**Basic usage:**

```tsx
import { useTranslate } from '@v-miniapp/ui-react'

function MyComponent() {
  const t = useTranslate()

  return (
    <div>
      <h1>{t('app.title')}</h1>
      <p>{t('user.greeting', { name: 'John' })}</p>
    </div>
  )
}
```

**With template params:**

```tsx
t('user.greeting', { name: 'John' })
// Returns: "Xin chào John!" (vi) or "Hello John!" (en)
```

---

## Language Management

**When to use:** Get or change current language.

**Import:** `import { useLanguage, setLanguage, getLanguage } from '@v-miniapp/ui-react'`

**Hook usage:**

```tsx
import { useLanguage } from '@v-miniapp/ui-react'

function LanguageSwitcher() {
  const { language, setLanguage } = useLanguage()

  return <Button onClick={() => setLanguage('en')}>Current: {language}</Button>
}
```

**Standalone functions:**

```tsx
import { getLanguage, setLanguage } from '@v-miniapp/ui-react'

const currentLang = getLanguage()
setLanguage('en')
```

---

## Standalone Translation

**When to use:** Translate outside React components.

**Import:** `import { translate } from '@v-miniapp/ui-react'`

**Usage:**

```tsx
import { translate } from '@v-miniapp/ui-react'

const text = translate('app.title')
const greeting = translate('user.greeting', { name: 'John' }, 'en') // Specify language
```

**Note:** Standalone `translate` has no reactivity. Use `useTranslate()` hook in components for reactivity.

---

## Custom Languages & Keys

**When to use:** Add custom languages and type-safe translation keys.

**Step 1:** Create JSON files for translations:

```json
// locales/vi.json
{
  "app.title": "Ứng dụng",
  "user.greeting": "Xin chào {name}!"
}
```

**Step 2:** Declare module augmentation in `global.d.ts`:

```tsx
import '@v-miniapp/ui-react'
import vi from './locales/vi.json'

declare module '@v-miniapp/ui-react' {
  interface ICustomLocales {
    resource: typeof vi
    language: 'vi' | 'en' | 'jp'
  }
}
```

**Step 3:** Use in config:

```tsx
import vi from './locales/vi.json'
import en from './locales/en.json'
import jp from './locales/jp.json'

const localesConfig: ILocalesConfig = {
  defaultLanguage: 'vi',
  resources: { vi, en, jp },
}
```

**Result:** TypeScript will infer types for all translation keys and language codes.

---

## LocalesProvider (Standalone)

**When to use:** Use i18n without App component.

**Import:** `import { LocalesProvider } from '@v-miniapp/ui-react'`

**Usage:**

```tsx
import { LocalesProvider } from '@v-miniapp/ui-react'

function MyApp() {
  return (
    <LocalesProvider config={localesConfig}>
      {/* Your app content */}
    </LocalesProvider>
  )
}
```

**Note:** `LocalesProvider` initializes once on mount. Place at top-level of your app.

---

## Important Notes

- **Type safety:** Use module augmentation for type-safe translation keys.
- **Reactivity:** `useTranslate()` hook is reactive; standalone `translate()` is not.
- **Default languages:** `'vi'` and `'en'` are supported by default.
- **URL-based init:** Language can be set via URL `?langCode=en`.
- **Template params:** Use `{key}` syntax in translations, pass via second parameter.
