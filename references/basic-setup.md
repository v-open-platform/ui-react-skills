# Basic setup: dev, build, deploy & app config

This document covers the core workflow (dev, build, deploy) and app configuration for V-MiniApp. Two app config examples are included: one for a generic miniapp and one for an app using `@v-miniapp/ui-react`.

---

## Prerequisites

- **Node.js** LTS v22+
- **CLI** installed globally: `npm install -g @v-miniapp/cli`
- **Login** (required for create and deploy): `v-miniapp-cli login`

---

## Development

Run the dev server from the project root. The CLI starts both the Mini App server and the Simulator.

```bash
v-miniapp-cli dev
# or
vma-cli dev
```

- **Mini App server:** typically on a port in the range `8080–8999`.
- **Simulator server:** typically on a port in the range `3000–3999`.

Use the printed URL or QR code to open the app in V-App. Changes trigger hot reload.

---

## Styles (with or without Tailwind)

When using **@v-miniapp/ui-react**, pick one:

- **Without Tailwind:** In app entry (e.g. `main.tsx` or `App.tsx`): `import '@v-miniapp/ui-react/styles.css'`.
- **With Tailwind:** In your main CSS file (e.g. `index.css` or `tailwind.css`): `@import '@v-miniapp/ui-react/tailwind';` - do **not** also import `styles.css` (tailwind replaces it).

If the user already has Tailwind, use the tailwind import; otherwise use `styles.css`.

---

## Build

Produce a production bundle in the `dist` folder:

```bash
v-miniapp-cli build
```

The CLI uses the project’s Vite config and emits output to `dist`. The build also copies and processes `app-config.json` (e.g. to `dist/appConfig.json`).

---

## Deploy

After a successful build, deploy to V-App:

```bash
v-miniapp-cli deploy
```

Typical flow:

1. Validates version and config (e.g. `package.json`, `app-config.json`).
2. Runs `build` if needed.
3. Packages source and `dist` (respecting `.gitignore`).
4. Uploads to V-App.

You can manage and release versions in [Dev Center](https://console.v-app.vn/). For JS APIs to work correctly, ensure `appIdentifier` in `app-config.json` matches the app registered in Dev Center.

---

## App config

Configuration is stored in **`app-config.json`** at the project root. The CLI and runtime use it for identity, window behavior, and optional features (e.g. tab bar, quick actions).

### Example 1: Generic V-MiniApp

Minimal config for a standard miniapp:

```json
{
  "appIdentifier": "com.example.myapp",
  "appName": "My Mini App",
  "h5App": "YES",
  "window": {
    "defaultTitle": "My App",
    "transparentTitle": "always"
  }
}
```

| Field                     | Description                                                                                                                     |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `appIdentifier`           | Unique app ID; must match the app in Dev Center. Format: e.g. `com.example.app` (letters, numbers, dots, hyphens, underscores). |
| `appName`                 | Display name of the app.                                                                                                        |
| `h5App`                   | Set to `"YES"` for H5/miniapp.                                                                                                  |
| `window.defaultTitle`     | Default title for the native title bar.                                                                                         |
| `window.transparentTitle` | Title bar style; e.g. `"always"` for transparent.                                                                               |

---

### Example 2: App using @v-miniapp/ui-react

When using the `App` component from `@v-miniapp/ui-react`, the SDK provides its own **NavigationBar**. To avoid duplicating the title bar with the native one, hide the native title bar in `app-config.json`:

```json
{
  "appIdentifier": "com.example.ui-react-app",
  "appName": "UI React Mini App",
  "h5App": "YES",
  "window": {
    "defaultTitle": "",
    "transparentTitle": "always"
  }
}
```

- **`defaultTitle": ""`** and **`transparentTitle": "always"`** keep the native title bar hidden so only the ui-react NavigationBar is shown.

If you use a non-empty `defaultTitle` or a different `window` setup, the native bar may appear alongside the ui-react bar; for ui-react apps, prefer the config above.

---

## Optional: tab bar and quick actions

The CLI can generate tab bar and quick-action assets from `app-config.json` if you define:

- **`tabBar`** - for bottom tab navigation.
- **`quickActions`** - for quick action entries (with optional `image` paths).

Structure and behavior are documented in the CLI and build plugins; keep `appIdentifier` and `appName` valid for deploy and JS API usage.
