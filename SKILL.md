---
name: v-miniapp-ui-react
description: Build and refactor mini-app UIs with `@v-miniapp/ui-react`, including app config, routing, i18n, page layout, design tokens, and SDK components. Use this skill whenever the user mentions `@v-miniapp/ui-react`, page structure, navigation bars, tabs, dark mode, pull-to-refresh, forms, icons, or wants raw HTML/CSS converted into library components, even if they only describe it as "mini-app UI".
---

# Overview

Use this skill for production-ready UI work built on `@v-miniapp/ui-react`.

This skill is the UI-focused counterpart to the broader mini-app workflow. Use it when the task is mainly about screen structure, navigation, theming, component choice, or app-level React configuration. If the task is mainly about CLI bootstrap, login, build/deploy, or `@v-miniapp/apis`, prefer the dedicated mini-app skill.

# Process

## Phase 1: Scope the UI Work

- Identify whether the task is primarily about one of these areas:
  - App shell and page registration
  - Routing and navigation
  - Localization
  - Theming and design tokens
  - Choosing or correcting `@v-miniapp/ui-react` components
- First decide whether the current project is a regular mini-app UI or an AI app UI.
- Treat it as an AI app when the workspace structure looks like `server/`, `web/`, `skills/`, and `app-config.json`.
- In AI app projects, `@v-miniapp/ui-react` is usually used inside widgets under `web/src/widgets/`, so do not assume the project needs `App` initialization, page registration, or mini-app routing setup.
- Read only the relevant reference files instead of loading everything up front.

## Phase 2: Apply Framework Conventions

### 2.1 App structure

- Follow [App setup](./references/app/setup.md) for `App` initialization, `pages`, layouts, keep-alive, navigation bar, and page layout only for regular mini-apps that actually use the `App` shell.
- Follow [Routing](./references/app/routing.md) for navigation patterns and page params only when the project is using mini-app app-level routing.
- If the project is an AI app with UI code inside `web/src/widgets/`, skip app setup and routing guidance unless the user is explicitly working on a standalone mini-app shell inside that project.
- Treat routing as single-level unless the docs say otherwise; prefer params/query-style navigation over invented nested route structures when routing is actually in play.
- Follow [Locale for AI apps](./references/ai-guidelines/locale.md) when the project is an AI app with `web/src/locales/`.
- Follow [Locale for Mini apps](./references/app/locale.md) when the task involves translations or language switching in a regular mini-app `App` shell.

### 2.2 Component system

- Follow [Component guidelines](./references/ai-guidelines/components.md) before adding or changing UI.
- Prefer `@v-miniapp/ui-react` components over raw HTML or custom-styled replacements.
- Verify props and icon names against the matching component reference before finalizing code.
- Reuse built-in layout and feedback patterns rather than rebuilding them from scratch.

### 2.3 Theme and styling

- Follow [App guidelines](./references/ai-guidelines/app.md) for framework limitations and theme expectations.
- Follow [Design tokens](./references/design-tokens.md) for colors, token usage, and theming.
- Keep styling aligned with the SDK design system; prefer component props and token-based styles over ad-hoc CSS.

## Phase 3: Validate the Result

- Check that every UI element uses the most appropriate `@v-miniapp/ui-react` primitive available.
- Verify component props, icon names, navigation setup, and app config values against the references.
- Avoid unsupported routing patterns, duplicated navigation bars, or custom styling that bypasses the design tokens without a reason.
- If the task also touches CLI setup or `@v-miniapp/apis`, coordinate with the dedicated mini-app skill instead of overloading this one.

# Reference Files

Use the bundled reference files under `packages/skills/ui-react/references/` and load only what matches the task.

## Core guidance

- [Component guidelines](./references/ai-guidelines/components.md) - preferred component usage and prop verification.
- [App guidelines](./references/ai-guidelines/app.md) - routing constraints and theme defaults.
- [Locale guidelines](./references/ai-guidelines/locale.md) - AI app widget locale setup with `web/src/locales/` and `initLocales(...)`.

## App framework

- [App setup](./references/app/setup.md) - `App` config, pages, layouts, keep-alive, and app-level options for regular mini-apps, not widget-only AI app UIs.
- [Routing](./references/app/routing.md) - links, navigation, page params, and lifecycle patterns when the project actually uses mini-app routing.
- [Locale](./references/app/locale.md) - i18n setup for regular mini-apps that pass `localesConfig` into `App`.

## Design system

- [Design tokens](./references/design-tokens.md) - token catalog, usage patterns, and theme overrides.

## Components

- [Foundation](./references/components/foundation.md) - typography and icon basics.
- [Icon names](./references/components/icon-names.md) - valid icon identifiers.
- [Actions](./references/components/actions.md) - buttons and action affordances.
- [Form](./references/components/form.md) - inputs, text areas, uploaders, calendars, and related controls.
- [Selections](./references/components/selections.md) - radio, checkbox, switch, chip, and option items.
- [Navigation](./references/components/navigation.md) - navigation bar and tab components.
- [Interface elements](./references/components/interface-elements.md) - avatar, carousel, and section patterns.
- [Feedback](./references/components/feedback.md) - toast, alert, and tooltip patterns.
- [Modal](./references/components/modal.md) - dialog and sheet usage.
- [Indicator](./references/components/indicator.md) - badges and state indicators.
