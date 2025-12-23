# Segment 1: Architecture Shift

**Duration: 20 minutes**

---

## Learning Objectives

By the end of this segment, you will:
- Understand the rules hierarchy (global → workspace)
- Create your first GEMINI.md file
- Know when rules apply vs when workflows apply

---

## The Rules Hierarchy

```
~/.gemini/GEMINI.md                    # Global rules (all projects)
    ↓
.agent/rules/*.md                       # Workspace rules (this project)
    ↓
Conversation context                    # What you say in chat
```

**Rules flow down. More specific overrides more general.**

---

## GEMINI.md: Your Global Brain

Location: `~/.gemini/GEMINI.md`

This file is loaded for EVERY agent conversation. Use it for:
- Your coding style preferences
- Safety constraints that always apply
- Patterns you want everywhere

### Example GEMINI.md

```markdown
# Global Rules

## Code Style
- Use TypeScript for all JavaScript projects
- Prefer functional components in React
- Always include error handling

## Safety
- Never run `rm -rf` without confirmation
- Never commit secrets or API keys
- Always create a backup before destructive operations

## Communication
- Explain what you're about to do before doing it
- Ask for clarification if requirements are ambiguous
- Summarize changes after completing a task

## Testing
- Write tests for new functions
- Run tests before marking task complete
```

---

## Workspace Rules

Location: `.agent/rules/*.md` (in project root)

These rules apply only to the current project. Use for:
- Project-specific conventions
- Tech stack requirements
- Team patterns

### Example Workspace Rules

```markdown
# Project: E-commerce App

## Stack
- Frontend: Next.js 14 with App Router
- Backend: Prisma with PostgreSQL
- Styling: Tailwind CSS

## Conventions
- API routes go in `app/api/`
- Components in `components/` with PascalCase
- Utilities in `lib/` with camelCase

## Database
- Always use transactions for multi-table operations
- Include migration files for schema changes
- Never delete production data

## Deployment
- Test in staging before production
- Use environment variables for secrets
- Keep production logs clean
```

---

## Rules vs Workflows

| Aspect | Rules | Workflows |
|--------|-------|-----------|
| **Purpose** | Shape behavior | Trigger actions |
| **When loaded** | Always active | On `/command` |
| **Scope** | Background context | Foreground action |
| **Example** | "Use TypeScript" | "/deploy to staging" |

**Rules are passive. Workflows are active.**

---

## Creating Your GEMINI.md

### Step 1: Open the file

```bash
# Create if doesn't exist
mkdir -p ~/.gemini
touch ~/.gemini/GEMINI.md
```

Or in Antigravity:
1. Cmd + Shift + P
2. "Open GEMINI.md"

### Step 2: Start with basics

```markdown
# Global Rules

## Style
- [Your language preference]
- [Your framework preference]
- [Your formatting preference]

## Safety
- [What should never happen automatically]
- [What always needs confirmation]

## Communication
- [How you want agent to communicate]
```

### Step 3: Add as you learn

Every time you find yourself repeating an instruction, add it to GEMINI.md.

---

## The Progressive Loading Model

```
Level 1: GEMINI.md           → Always loaded
Level 2: Workspace rules     → Loaded for this project
Level 3: Conversation        → Current context
```

**Token budget**: Rules consume tokens. Keep them concise.

---

## Anti-Patterns

### Too Verbose

```markdown
# Bad: Essay in rules
When you're writing code, I want you to think very carefully
about the implications of each line and ensure that you're
following best practices as defined by the community...
```

### Too Vague

```markdown
# Bad: Meaningless rules
- Write good code
- Be helpful
- Don't make mistakes
```

### Too Restrictive

```markdown
# Bad: Micromanagement
- Always use exactly 2 spaces for indentation
- Never use arrow functions
- Always add comments to every line
```

---

## Good Rule Patterns

### Specific and Actionable

```markdown
- Use `async/await` instead of `.then()` chains
- Include `try/catch` for all async operations
- Log errors with context: `logger.error({ context, error })`
```

### Safety Constraints

```markdown
## NEVER (without explicit confirmation)
- Delete files matching `*.sql` or `*.db`
- Run commands with `sudo`
- Modify `.env` files

## ALWAYS
- Create backup before database migrations
- Run tests before marking task complete
```

### Communication Patterns

```markdown
## Before Starting
- State what you're about to do
- List files you'll modify

## After Completing
- Summarize changes made
- Note any follow-up actions needed
```

---

## Pause Point #1

**Time to practice: 3 minutes**

Go to [exercises/01-gemini-md/](../exercises/01-gemini-md/) and create your GEMINI.md.

---

## Checkpoint

You should now understand:

- [ ] Where GEMINI.md lives (`~/.gemini/GEMINI.md`)
- [ ] Where workspace rules live (`.agent/rules/`)
- [ ] The difference between rules and workflows
- [ ] How to write effective rules

---

## Next

**[Segment 2: Your First Workflow →](./02-first-workflow.md)**

Learn to create reusable prompts triggered with `/`.
