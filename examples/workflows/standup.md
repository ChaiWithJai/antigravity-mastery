# Daily Standup Generator

Generate a standup update from my recent activity.

## Steps

### 1. Check Recent Git Activity
- Run `git log --oneline --since="24 hours ago" --author="$(git config user.email)"`
- Note all commits made
- Identify completed work

### 2. Check Current Branch
- Run `git branch --show-current`
- Run `git status`
- Identify work in progress
- Note any uncommitted changes

### 3. Check for Issues
- Look for failing tests: `npm test 2>&1 | tail -20`
- Search for TODO/FIXME in recent changes
- Identify any blockers

## Output Format

```markdown
## Standup - [Today's Date]

**Yesterday:**
- [Completed item 1]
- [Completed item 2]

**Today:**
- [Planned work based on current branch/status]

**Blockers:**
- [Any issues found, or "None"]
```

## Rules
- Maximum 3 items per section
- Use past tense for Yesterday
- Use future tense for Today
- Be specific but concise
- If no activity found, say so honestly
