---
name: "Update ClickUp Task"
description: "Efficiently update ClickUp tasks with status, assignees, dates, priority, custom fields, and comments using structured patterns"
alwaysAllow: ["Bash"]
---

# ClickUp Task Update Skill

Use this skill to modify ClickUp tasks programmatically. Whether you need to move a task through workflow states, assign work, set timelines, or add progress notes, this skill provides patterns and best practices.

## When to Use This Skill

- Updating task status through workflow (to do → in progress → on review → done)
- Assigning tasks to team members
- Setting deadlines and time estimates
- Updating priority levels
- Modifying custom fields (Repository, Update, documentations)
- Adding comments and descriptions to track progress
- Bulk updating multiple task properties at once

## Common Update Patterns

### Pattern 1: Update Status
Transition tasks through your workflow states:

```javascript
// Move task to next stage
clickup_update_task({
  task_id: "86ewja1g1",
  status: "in progress"  // Options: to do, in progress, on review, done, etc.
})
```

### Pattern 2: Assign & Estimate
Assign work to team members and set time estimates:

```javascript
clickup_update_task({
  task_id: "86ewja1g1",
  assignees: ["101639797"],  // User IDs, emails, or "me"
  time_estimate: "480"       // Minutes (480 = 8 hours)
})
```

### Pattern 3: Set Dates & Priority
Define project timeline and task importance:

```javascript
clickup_update_task({
  task_id: "86ewja1g1",
  start_date: "2026-02-15",  // ISO format: YYYY-MM-DD
  due_date: "2026-02-25",
  priority: "high"           // Options: urgent, high, normal, low
})
```

### Pattern 4: Update Custom Fields
Modify workspace-specific fields (Repository, Update, documentations):

```javascript
clickup_update_task({
  task_id: "86ewja1g1",
  custom_fields: [
    { id: "26b326c3-...", value: "archipelago-mobile-repo" },
    { id: "dd51d405-...", value: "Implemented search with map integration" },
    { id: "a30c8bf2-...", value: "https://docs.example.com/search" }
  ]
})
```

### Pattern 5: Update Name & Description
Modify task content:

```javascript
clickup_update_task({
  task_id: "86ewja1g1",
  name: "Feat: Search Function with Map View",
  description: "Implement location-based search with interactive map",
  markdown_description: "## Overview\n\nAdd search capabilities..."
})
```

### Pattern 6: Bulk Update
Update multiple properties simultaneously:

```javascript
clickup_update_task({
  task_id: "86ewja1g1",
  status: "in progress",
  assignees: ["101639797"],
  priority: "high",
  due_date: "2026-02-25",
  time_estimate: "480",
  tags: ["frontend", "mobile"]
})
```

## Key Guidelines

1. **Task IDs**: Always use the correct ClickUp task ID (format: alphanumeric, e.g., "86ewja1g1")
2. **Date Format**: Use ISO format for dates: YYYY-MM-DD (e.g., "2026-02-25")
3. **Time Estimates**: Specify in minutes (480 = 8 hours, 120 = 2 hours)
4. **Custom Fields**: Reference by ID from your workspace schema
5. **Assignees**: Use user IDs, emails, or "me" for current user
6. **Statuses**: Use valid workflow states from your ClickUp workspace

## Your Custom Fields (Ready to Use)

- **Repository**: Link to code repository or project reference
- **Update**: Progress notes and implementation details
- **documentations**: Documentation URL or link

## Best Practices

1. **Verify before updating**: Get task details first to understand current state
2. **Use descriptive values**: When updating custom fields, provide clear, actionable information
3. **Set realistic dates**: Ensure due dates align with actual project timelines
4. **Assign promptly**: Assign tasks immediately when moving to "in progress"
5. **Document changes**: Use comments or description updates to track what changed and why
6. **Batch operations**: Combine multiple updates in one API call for efficiency

## What to Avoid

- Don't update without understanding the current task state
- Don't set past due dates without explicit user confirmation
- Don't reassign tasks without notifying the assignee
- Don't use ambiguous dates—always use ISO format (YYYY-MM-DD)
- Don't forget to include full custom field IDs when updating custom fields
- Don't overwrite existing values without confirmation unless explicitly requested

## Workflow Example

When updating a task during active development:

1. **Get task details** to understand current state
2. **Update status** to "in progress"
3. **Assign to developer** if not already assigned
4. **Set realistic due date** based on scope
5. **Update custom fields** with progress notes
6. **Add comment** summarizing changes

## Available Tools

- `clickup_get_task` - Retrieve complete task details
- `clickup_update_task` - Modify task properties
- `clickup_create_task_comment` - Add comments to task
- `clickup_search` - Find tasks by criteria

## Tips for Success

- **Priority levels**: Use sparingly—mark only truly urgent/high-priority work
- **Time estimates**: Be realistic and account for testing/review time
- **Custom fields**: Keep updates concise but informative
- **Descriptions**: Use markdown formatting for better readability
- **Comments**: Add context about why changes were made, not just what changed
