# Segment 2: Your First Workflow

**Duration: 35 minutes**

---

## Learning Objectives

By the end of this segment, you will:
- Create a workflow file that triggers with `/`
- Understand workflow anatomy
- Build a workflow for a common task you do

---

## What Are Workflows?

Workflows are saved prompts you trigger with `/command`.

```
You: /deploy
Agent: [Executes your deployment workflow]
```

**Think of workflows as macros for your agent.**

---

## Workflow Locations

| Type | Location | Trigger |
|------|----------|---------|
| Global | `~/.gemini/antigravity/global_workflows/*.md` | Available everywhere |
| Workspace | `.agent/workflows/*.md` | Only in this project |

---

## Workflow Anatomy

```markdown
# deploy.md

## Deployment Workflow

### Pre-flight Checks
1. Run all tests
2. Check for uncommitted changes
3. Verify environment variables

### Deployment Steps
1. Build the project: `npm run build`
2. Run database migrations
3. Deploy to staging first
4. Run smoke tests on staging
5. If smoke tests pass, deploy to production

### Post-deployment
1. Verify production is running
2. Check error monitoring for new errors
3. Notify team in Slack

### Rollback (if needed)
If errors detected:
1. Revert to previous version
2. Notify team immediately
3. Create incident report
```

When you type `/deploy`, this entire workflow becomes the agent's instructions.

---

## Creating Your First Workflow

### Step 1: Create workflow directory

```bash
# Global workflows
mkdir -p ~/.gemini/antigravity/global_workflows

# Workspace workflows
mkdir -p .agent/workflows
```

### Step 2: Create workflow file

```bash
# Example: standup workflow
touch ~/.gemini/antigravity/global_workflows/standup.md
```

### Step 3: Write the workflow

```markdown
# standup.md

## Daily Standup Generator

Look at my recent git activity and generate a standup update.

### Steps
1. Check git log for commits in last 24 hours
2. Check current branch and any in-progress work
3. Look for any failing tests or TODOs

### Output Format
Generate in this format:

**Yesterday:**
- [What I completed]

**Today:**
- [What I'm working on]

**Blockers:**
- [Any blockers, or "None"]

Keep it concise. No more than 3 bullets per section.
```

### Step 4: Use the workflow

```
You: /standup
Agent: [Analyzes git, generates standup]
```

---

## Workflow Patterns

### Task Automation

```markdown
# pr-review.md

## PR Review Workflow

1. Fetch the PR diff
2. Analyze changes for:
   - Security issues
   - Performance problems
   - Code style violations
   - Missing tests
3. Generate review comments
4. Summarize overall assessment
```

### Code Generation

```markdown
# component.md

## React Component Generator

Create a new React component with:
1. TypeScript types
2. Props interface
3. Styled components
4. Unit test file
5. Storybook story

Ask me for:
- Component name
- Props it needs
- Whether it's a page or reusable component
```

### Research & Analysis

```markdown
# investigate.md

## Investigation Workflow

When I say /investigate [topic]:
1. Search the codebase for related code
2. Find relevant documentation
3. Check git history for context
4. Summarize findings
5. Suggest next steps
```

### Maintenance

```markdown
# cleanup.md

## Code Cleanup Workflow

1. Find unused imports
2. Remove dead code
3. Fix linting errors
4. Update outdated dependencies (non-breaking)
5. Run tests to verify nothing broke
6. Create a summary of changes
```

---

## Workflow with Parameters

Workflows can accept parameters:

```markdown
# ticket.md

## Ticket Implementation

When I say /ticket [number]:
1. Fetch ticket details from issue tracker
2. Create a new branch: `feature/ticket-[number]`
3. Generate implementation plan
4. Ask for approval before coding
5. Implement the ticket
6. Write tests
7. Create PR with ticket reference
```

Usage:
```
/ticket 1234
```

---

## Workflow Best Practices

### 1. Be Specific About Output

```markdown
# Bad
Generate a report.

# Good
Generate a report with:
- Summary (3 sentences max)
- Key metrics in a table
- Action items as checkboxes
```

### 2. Include Verification Steps

```markdown
# Good
After making changes:
1. Run tests: `npm test`
2. If tests fail, fix before proceeding
3. Take screenshot of working feature
```

### 3. Define Rollback

```markdown
# Good
If something goes wrong:
1. Revert changes: `git checkout .`
2. Report what failed
3. Suggest alternative approach
```

### 4. Set Boundaries

```markdown
# Good
## What This Workflow Does
- Creates new components
- Writes tests

## What This Workflow Does NOT Do
- Modify existing components
- Delete files
- Push to remote
```

---

## Workflow Discovery

List available workflows:
```
You: What workflows are available?
Agent: [Lists global and workspace workflows]
```

Or type `/` and wait for autocomplete.

---

## Pause Point #2

**Time to practice: 5 minutes**

Go to [exercises/02-first-workflow/](../exercises/02-first-workflow/) and create a workflow for something you do often.

---

## Checkpoint

You should now be able to:

- [ ] Create a workflow file in the right location
- [ ] Write clear, actionable workflow instructions
- [ ] Trigger workflows with `/command`
- [ ] Include verification steps in workflows

---

## Next

**[Segment 3: Agent Manager →](./03-agent-manager.md)**

Learn to orchestrate multiple agents working in parallel.
