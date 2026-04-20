---
name: "GitHub PR"
description: "Create pull requests with auto-assignment, review requests, and template enforcement using GitHub MCP"
alwaysAllow: ["mcp__github__create_pull_request", "mcp__github__update_pull_request", "mcp__github__search_pull_requests", "mcp__github__get_me"]
---

# GitHub Pull Request Skill

This skill automates pull request creation with GitHub MCP integration, ensuring proper template compliance, auto-assignment of reviewers, and automatic review requests.

## Workflow

When creating a PR, follow this process:

### 1. Gather Required Information
- **Repository**: owner/repo
- **Branch**: feature branch name (head)
- **Base branch**: target branch (usually `main`)
- **Title**: Clear, concise PR title (under 70 characters)
- **Description**: Detailed explanation of changes
- **Reviewers**: List of GitHub usernames to request reviews from

### 2. PR Template Compliance

Every PR **must** include the following structure in the description:

```markdown
## Description
[Brief description of the changes]

## Related Issue
Closes #[issue-number]

## Type of Change
- [ ] 🐛 Bug fix (non-breaking change which fixes an issue)
- [ ] ✨ New feature (non-breaking change which adds functionality)
- [ ] 💥 Breaking change (fix or feature that would cause existing functionality to change)
- [ ] 📝 Documentation update
- [ ] ♻️ Code refactoring
- [ ] 🧪 Test addition/update
- [ ] 🔧 Configuration/Build change
- [ ] 🚀 Performance improvement

## Checklist
- [ ] I have performed a self-review of my own code
- [ ] I have made corresponding changes to the documentation
- [ ] I have added tests that prove my fix is effective or that my feature works
- [ ] New and existing unit tests pass locally with my changes
```

**Important**: Always include at least one checkbox marked in the "Type of Change" section.

### 3. Auto-Assignment Process

Before creating the PR:

1. **Identify reviewers** - Determine appropriate team members based on:
   - Code ownership files (CODEOWNERS)
   - Team members familiar with the feature area
   - Project maintainers

2. **Use GitHub MCP** - Call `mcp__github__update_pull_request` to assign reviewers:
   ```
   owner: "repository-owner"
   repo: "repository-name"
   pullNumber: [PR number]
   reviewers: ["github-username-1", "github-username-2"]
   ```

3. **Request reviews** - Use `mcp__github__get_me` first to understand available team members

### 4. PR Creation Steps

1. **Validate all required fields** are present (title, description, issue link)
2. **Format the description** according to template
3. **Create the PR** using `mcp__github__create_pull_request`:
   ```
   owner: "repository-owner"
   repo: "repository-name"
   title: "Your PR title"
   head: "feature-branch"
   base: "main"
   body: "Full description following template"
   ```
4. **Auto-request reviews** using `mcp__github__update_pull_request` with reviewers array
5. **Confirm success** and provide PR URL to user

## Best Practices

### Title Guidelines
- Use imperative mood: "Add feature" not "Added feature"
- Keep under 70 characters
- Start with type prefix: `feat:`, `fix:`, `docs:`, `refactor:`, etc.
- Examples:
  - `feat: add hotel search map view`
  - `fix: resolve card selection bug`
  - `docs: update installation guide`

### Description Guidelines
- Be specific about what changed and why
- Link to related issues with "Closes #123"
- Explain the reasoning behind decisions
- Mention any breaking changes
- Include testing notes if applicable

### Reviewer Selection
- Assign 1-3 reviewers depending on change scope
- Prefer recent contributors to the changed files
- Include at least one team lead or maintainer
- For breaking changes, assign broader team review

## Error Handling

- **Missing template fields**: Reject and ask user to provide required sections
- **Invalid issue number**: Warn if issue link format is incorrect
- **Reviewer not found**: Verify GitHub usernames before assignment
- **PR already exists**: Check for existing PRs on the branch before creating

## Examples

### Creating a Feature PR

```
User Request: "Create a PR for the search map feature"

Task:
1. Verify feature branch exists
2. Create PR with:
   - Title: "feat: implement hotel search map view"
   - Description: (following template with description, issue link, feature type)
   - Reviewers: ["project-lead", "map-expert"]
3. Auto-request reviews
4. Return PR URL
```

### Creating a Bug Fix PR

```
User Request: "Create PR to fix the selection bug"

Task:
1. Verify bug fix branch exists
2. Create PR with:
   - Title: "fix: resolve card selection not updating UI"
   - Description: (following template with bug fix type)
   - Reviewers: ["qa-lead", "dev-lead"]
3. Auto-request reviews
4. Return PR URL
```

## Workflow Integration

This skill integrates with:
- **GitHub MCP**: All PR operations (create, update, request reviews)
- **PR Template**: Ensures compliance with project standards
- **Team collaboration**: Automates reviewer assignment

## Co-Authorship

Always include Craft Agent as co-author in commit messages:
```
Co-Authored-By: Craft Agent <agents-noreply@craft.do>
```
