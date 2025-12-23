# Exercise 2: Create Your First Workflow

**Duration: 5 minutes**

---

## Objective

Create a workflow for something you do frequently, triggered with `/`.

---

## Steps

### Step 1: Identify a repetitive task

Think of something you do often:
- Daily standup
- PR review
- Project setup
- Code review
- Debugging process
- Deployment

### Step 2: Create workflow file

```bash
mkdir -p ~/.gemini/antigravity/global_workflows
touch ~/.gemini/antigravity/global_workflows/[name].md
```

For example:
```bash
touch ~/.gemini/antigravity/global_workflows/standup.md
```

### Step 3: Write the workflow

Include:
1. **Purpose**: What this workflow does
2. **Steps**: Specific actions to take
3. **Output format**: Expected result structure
4. **Verification**: How to confirm success

### Step 4: Test the workflow

1. Open Agent Manager
2. Type `/[workflow-name]`
3. Verify workflow executes as expected

---

## Success Criteria

- [ ] Workflow file exists in `global_workflows/`
- [ ] Workflow triggers with `/name`
- [ ] Workflow produces expected output

---

## Ideas for Workflows

| Workflow | Purpose |
|----------|---------|
| `/standup` | Generate daily standup from git activity |
| `/review` | Run code review checklist |
| `/setup` | Initialize new project with your standards |
| `/debug` | Walk through debugging process |
| `/doc` | Generate documentation for current file |

---

## Example

See [solution/standup.md](./solution/standup.md) for a complete example.
