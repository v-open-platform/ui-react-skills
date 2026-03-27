# V MiniApp UI React Skill

Build and refine mini-app UIs with `@v-miniapp/ui-react` — a React component library with 60+ components, design tokens, routing, and i18n for the V-App platform.

## Features

- **60+ UI Components** - Button, TextField, Modal, Tabs, Avatar, Calendar, Carousel, and more
- **Design Token System** - Semantic color tokens, typography, spacing aligned with V-App standards
- **App Shell & Routing** - Single-level routing, navigation bar, bottom tabs, page lifecycle
- **Localization (i18n)** - Built-in translation hooks for multi-language support
- **Dark Mode** - Theme-aware components with design token integration
- **AI App Support** - Guidelines for using components inside AI app widgets

## Installation

### Option 1: Using skills CLI (Recommended)

```bash
# Install to current project
npx skills add v-open-platform/ui-react-skills

# Install globally
npx skills add v-open-platform/ui-react-skills -g

# Install for specific agent
npx skills add v-open-platform/ui-react-skills -a claude-code
```

### Option 2: Manual Installation

**For Claude Code:**

```bash
git clone <repo-url> ui-react-skills
cp -r ui-react-skills/skills/v-miniapp-ui-react ~/.claude/skills/
```

**For Project-level:**

```bash
mkdir -p .claude/skills
cp -r ui-react-skills/skills/v-miniapp-ui-react .claude/skills/
```

## Supported Agents

| Agent          | Skills Directory                         |
| -------------- | ---------------------------------------- |
| Claude Code    | `~/.claude/skills/` or `.claude/skills/` |
| Cursor         | `~/.cursor/skills/` or `.cursor/skills/` |
| OpenCode       | `~/.opencode/skill/`                     |
| GitHub Copilot | `.github/copilot/skills/`                |
| Windsurf       | `~/.windsurf/skills/`                    |

## Usage

Once installed, the skill activates automatically when you:

- Build UIs with `@v-miniapp/ui-react` components
- Set up app shell, pages, and navigation
- Work with routing and page params
- Apply design tokens and theming
- Convert raw HTML/CSS to library components
- Configure localization and translations

### Example Prompts

- "Create a product list page with bottom navigation"
- "Add a form with text input, date picker, and dropdown"
- "Convert this HTML to `@v-miniapp/ui-react` components"
- "Set up dark mode with design tokens"
- "Add Vietnamese and English translations to my app"

## Skill Structure

```
v-miniapp-ui-react/
├── SKILL.md                          # Main skill file
└── references/
    ├── basic-setup.md                # Dev workflow & app config
    ├── design-tokens.md              # Color tokens, typography, theming
    ├── ai-guidelines/
    │   ├── app.md                    # Routing constraints & theme defaults
    │   ├── components.md             # Component usage rules
    │   └── locale.md                 # AI app locale setup
    ├── app/
    │   ├── setup.md                  # App shell, pages, layouts
    │   ├── routing.md                # Navigation & page params
    │   └── locale.md                 # Mini-app i18n setup
    └── components/
        ├── foundation.md             # Typography & Icon
        ├── icon-names.md             # 100+ icon identifiers
        ├── actions.md                # Button variants
        ├── form.md                   # TextField, DatePicker, Uploader, etc.
        ├── selections.md             # Radio, Checkbox, Switch, Chip
        ├── navigation.md             # NavigationBar, BottomTabBar, TabBar
        ├── interface-elements.md     # Avatar, Carousel, Section
        ├── feedback.md               # Toast, Alert, Tooltip
        ├── modal.md                  # Dialog & Sheet
        └── indicator.md              # Badge & BadgeContainer
```

## Component Categories

| Category       | Components                                                                                                 |
| -------------- | ---------------------------------------------------------------------------------------------------------- |
| **Foundation** | Typography, Icon                                                                                           |
| **Actions**    | Button (solid, outline, ghost)                                                                             |
| **Form**       | TextField, NumberField, DateField, SearchField, TextArea, Dropdown, DatePicker, Calendar, Uploader, Rating |
| **Selections** | Radio, Checkbox, Chip, Switch, OptionItem                                                                  |
| **Navigation** | NavigationBar, BottomTabBar, TabBar                                                                        |
| **Interface**  | Avatar, Carousel, Section                                                                                  |
| **Feedback**   | Toast, Alert, Tooltip                                                                                      |
| **Modal**      | Dialog, Sheet                                                                                              |
| **Indicator**  | Badge, BadgeContainer                                                                                      |

## Related Skills

| Skill         | Purpose                                                                            |
| ------------- | ---------------------------------------------------------------------------------- |
| **v-miniapp** | CLI tooling, build/deploy, native APIs with `@v-miniapp/cli` and `@v-miniapp/apis` |
| **ai-app**    | MCP-based AI apps with `@v-miniapp/ai` server/web/apis modules                     |

## Resources

- [Developer](https://developer.v-app.vn/)
- [V-App](https://v-app.vn/)
- [Agent Skills Specification](https://agentskills.io/specification)

## License

MIT
