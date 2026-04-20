# claude-m-skills

A collection of Craft Agent skills for Flutter development and project management workflows.

## Structure

```
├── global/          # Global skills (available across all workspaces)
│   ├── flutter-animations/
│   ├── flutter-architecture/
│   └── flutter-expert/
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
| **flutter-expert** | Senior Flutter developer guidance — Riverpod/Bloc, GoRouter, performance optimization |

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
