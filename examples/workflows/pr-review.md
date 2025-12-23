# PR Review Workflow

Review a pull request thoroughly and provide actionable feedback.

## Input
When triggered, ask for:
- PR URL or number
- Repository (if not obvious from context)

## Review Process

### 1. Fetch PR Details
- Get PR description and context
- Identify what problem this solves
- Check if there's a linked issue

### 2. Review Changes
For each changed file, check:

**Code Quality**
- Does the code follow team conventions?
- Is naming clear and consistent?
- Are there magic numbers or hardcoded values?

**Logic**
- Is the logic correct?
- Are edge cases handled?
- Any potential bugs?

**Security**
- Input validation present?
- No secrets or credentials?
- SQL injection / XSS risks?

**Performance**
- N+1 queries?
- Unnecessary loops?
- Memory leaks?

**Testing**
- Are new functions tested?
- Do existing tests still pass?
- Edge cases covered?

### 3. Overall Assessment

Rate as:
- **Approve**: Ready to merge
- **Request Changes**: Must fix before merge
- **Comment**: Questions or suggestions (non-blocking)

## Output Format

```markdown
## PR Review: #{number}

### Summary
[What this PR does in 1-2 sentences]

### Overall Assessment
[Approve / Request Changes / Comment]

### Blocking Issues
- [ ] [Issue that must be fixed]
- [ ] [Issue that must be fixed]

### Suggestions (Non-Blocking)
- [Improvement idea]
- [Improvement idea]

### Questions
- [Clarification needed]

### Tested
- [ ] Builds successfully
- [ ] Tests pass
- [ ] Manually verified (if applicable)
```

## Rules
- Be specific with line references
- Suggest improvements, don't just criticize
- Acknowledge good work when you see it
- If you're unsure about something, ask
