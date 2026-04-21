# claude-m-skills

A collection of Craft Agent skills for Flutter development and project management workflows.

## Structure

```
├── global/          # Global skills (available across all workspaces)
│   ├── flutter-animations/
│   ├── flutter-architecture/
│   ├── flutter-dot-shorthand/
│   ├── flutter-env-var/
│   ├── flutter-expert/
│   ├── flutter-extract-atomic-widgets/
│   ├── flutter-extract-i18n/
│   ├── flutter-feature-scaffold/
│   ├── flutter-freezed-model/
│   └── flutter-global-component/
└── workspace/       # Workspace-level skills
    ├── api-tester/
    ├── clickup-update/
    ├── git-commit/
    ├── github-pr/
    ├── pub-bumper/
    └── unit-tester/
```

## Skills

### Global Skills

| Skill | Description |
|-------|-------------|
| **flutter-animations** | Comprehensive guide for implementing animations in Flutter — implicit, explicit, hero, staggered, and physics-based |
| **flutter-architecture** | MVVM pattern and feature-first project organization for scalable Flutter apps |
| **flutter-dot-shorthand** | Migrate pages/widgets to Dart's dot-shorthand syntax (enum values, `EdgeInsets.all` → `.all`, named constructors) where the type is inferable |
| **flutter-env-var** | Add an envied-backed environment variable — appends to `.env`, registers in `app_env.dart`, runs code generation |
| **flutter-expert** | Senior Flutter developer guidance — Riverpod/Bloc, GoRouter, performance optimization |
| **flutter-extract-atomic-widgets** | Refactor a page into atomic widgets — `v_*.dart` views and `c_*.dart` components — and kill `_buildXxx()` helpers |
| **flutter-extract-i18n** | Extract hardcoded strings from pages/widgets into slang i18n JSONs, translate into all locales, and replace call sites with `context.slang.*` |
| **flutter-feature-scaffold** | Scaffold a Clean-Architecture feature folder tree (data + features layers) with starter files mirroring the chat feature |
| **flutter-freezed-model** | Generate a `@freezed` data model with converters and `@JsonKey` renames, per the `promotion_model.dart` convention |
| **flutter-global-component** | Create a new reusable `global_*.dart` widget under `shared/components/{displays,interactive,wrapper}/` using project design tokens |

### Workspace Skills

| Skill | Description |
|-------|-------------|
| **api-tester** | Test APIs with curl, analyze responses, and validate API behavior |
| **clickup-update** | Update ClickUp tasks with status, assignees, dates, priority, and custom fields |
| **git-commit** | Generate storytelling-focused Conventional Commits messages with context integration |
| **github-pr** | Create pull requests with auto-assignment, review requests, and template enforcement |
| **pub-bumper** | Autonomous Flutter dependency auditor — bumps safe package updates and creates PRs |
| **unit-tester** | Priority-based Flutter testing (Repository → State → Widget) |

## Usage

Each skill contains a `SKILL.md` file with full instructions. Many skills also include:
- `references/` — Detailed reference documentation
- `assets/` — Code templates and examples
- `icon.svg` — Visual icon for the skill

## Author

Skills maintained by [diptaarch](https://github.com/diptaarch).
