# Daily Standup Generator

Generate a standup update from my recent activity.

## Steps

### 1. Check Recent Git Activity
- Run `git log --oneline --since="24 hours ago"`
- Note all commits made
- Identify completed work

### 2. Check Current Branch
- Run `git branch --show-current`
- Run `git status`
- Note any work in progress

### 3. Check for Blockers
- Look for failing tests
- Check for TODO comments in recent changes
- Note any dependencies on others

## Output Format

Generate standup in this format:

```markdown
## Standup - [Today's Date]

**Yesterday:**
- [Completed item 1]
- [Completed item 2]

**Today:**
- [Planned item 1]
- [Planned item 2]

**Blockers:**
- [Blocker or "None"]
```

## Rules
- Keep each section to 3 items max
- Use past tense for Yesterday
- Use future tense for Today
- Be specific but concise
