# Locale Guidelines for AI Apps

Use this guide for AI app UIs that follow the `packages/skills/ai` project shape with `server/`, `web/`, `skills/`, and `app-config.json`.

This is different from [app locale](../app/locale.md):

- AI apps usually localize widget UIs under `web/src/` and do not pass `localesConfig` into a top-level mini-app `App`.
- Regular mini-app locale setup centers around `<App config={...} localesConfig={...} />`.
- AI apps typically initialize locales once from `web/src/locales/index.ts` with `initLocales(...)`.

---

## When To Use This Pattern

Use this AI app locale pattern when the workspace looks like:

```text
{project}/
├── server/
├── web/
│   └── src/
│       ├── widgets/
│       └── locales/
├── skills/
└── app-config.json
```

If the UI lives in `web/src/widgets/` and the project also has `server/` and `skills/`, treat it as an AI app and use this guide instead of the regular mini-app locale guide.

---

## Expected File Layout

Keep locale resources in the frontend `web` package:

```text
web/src/locales/
├── en.json
├── vi.json
└── index.ts
```

- `en.json` and `vi.json` contain translation strings.
- `index.ts` initializes locale resources once for the web bundle.

---

## Initialization Pattern

Template setup in `ai-app-blank` uses:

```ts
import { initLocales } from '@v-miniapp/ui-react'
import en from './en.json'
import vi from './vi.json'

initLocales({
  resources: { en, vi },
})
```

Guidelines:

- Initialize locales with `initLocales(...)` in `web/src/locales/index.ts`.
- Keep the initialization file small and declarative.
- Import locale setup once near the widget/web entry path so translations are ready before rendering UI.
- Do not rebuild a separate ad-hoc i18n system for AI app widgets.

---

## Translation Resource Rules

Follow the resource shape used by the AI app template:

```json
{
  "greet": "Greet",
  "greet.placeholder": "Enter a name...",
  "greet.result": "Result"
}
```

Guidelines:

- Keep keys flat with `string: string` pairs only.
- Do not use nested JSON objects for AI app locale files.
- Keep keys stable and small; prefer names like `feature.label`, `feature.placeholder`, `feature.result`.
- When adding a new key, update all supported language files together, at minimum `en.json` and `vi.json`.
- Keep the same key set across locales to avoid widget copy drifting by language.

---

## Widget Usage

Inside AI app widgets:

- Use the normal `@v-miniapp/ui-react` translation utilities after locale initialization is loaded.
- Translate user-facing labels, placeholders, button text, empty states, and result headings through locale keys instead of hardcoded strings.
- Keep widget copy in locale JSON files, not scattered across `web/src/widgets/*`.

If the widget is simple and only one language file was updated, add the missing keys to the companion locale file before finishing.

---

## What Not To Assume

- Do not assume AI apps use the mini-app `App` shell from [app locale](../app/locale.md).
- Do not require `localesConfig` unless the project clearly uses the regular mini-app `App` pattern.
- Do not mix widget-level AI app locale setup with unrelated app-level routing or page registration guidance.

---

## Quick Decision Rule

Choose the locale approach based on project shape:

- If the project uses `web/src/locales/index.ts` and widget UIs under `web/src/widgets/`, use this AI app locale pattern.
- If the project uses `<App config={...} localesConfig={...} />`, use [app locale](../app/locale.md) instead.
