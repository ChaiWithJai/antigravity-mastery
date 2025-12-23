# GEMINI.md Anatomy Reference

Quick reference for global and workspace rules.

---

## File Locations

| Type | Location | Scope |
|------|----------|-------|
| Global | `~/.gemini/GEMINI.md` | All projects |
| Workspace | `[project]/.agent/rules/*.md` | This project only |

---

## Hierarchy

```
GEMINI.md (global)
    ↓ loaded first
.agent/rules/*.md (workspace)
    ↓ loaded second, can override
Conversation context
    ↓ highest priority
```

**More specific overrides more general.**

---

## GEMINI.md Structure

```markdown
# Global Rules

## Code Style
[Language and formatting preferences]

## Safety
[What should never happen automatically]

## Communication
[How agent should interact]

## Testing
[Testing requirements]
```

---

## Recommended Sections

### Code Style
```markdown
## Code Style

### Languages
- Use TypeScript for JavaScript projects
- Use Python 3.11+ with type hints

### Formatting
- Use Prettier defaults
- Run formatters before committing

### Patterns
- Prefer functional over OOP
- Always handle errors explicitly
```

### Safety
```markdown
## Safety

### NEVER Auto-Execute
- `rm -rf` or recursive delete
- `--force` flags
- `sudo` commands
- Production deployments

### ALWAYS Confirm
- Database migrations
- Git push to main
- File deletions
```

### Communication
```markdown
## Communication

### Before Starting
- State what you're about to do
- List files you'll modify

### After Completing
- Summarize changes
- Note follow-up actions
```

### Testing
```markdown
## Testing
- Write tests for new functions
- Run tests before marking complete
- If tests fail, fix first
```

---

## Good Patterns

### Specific and Actionable
```markdown
# Good
- Use `async/await` instead of `.then()` chains
- Include `try/catch` for all async operations
- Log errors with context: `logger.error({ context, error })`
```

### NEVER/ALWAYS Format
```markdown
# Good
## NEVER (without explicit confirmation)
- Delete files matching `*.sql`
- Run commands with `sudo`

## ALWAYS
- Create backup before migrations
- Run tests before completion
```

### Clear Categories
```markdown
# Good
## Code Quality
[code-related rules]

## Git Workflow
[git-related rules]

## Security
[security-related rules]
```

---

## Anti-Patterns

### Too Vague
```markdown
# Bad
- Write good code
- Be helpful
- Don't make mistakes
```

### Too Verbose
```markdown
# Bad
When you're writing code, I want you to think very carefully
about the implications of each line and ensure that you're
following best practices as defined by the community and
documented in various style guides...
```

### Too Restrictive
```markdown
# Bad
- Always use exactly 2 spaces
- Never use arrow functions
- Always add comments to every line
- Ask permission for everything
```

---

## Workspace Rules

### Location
```
[project]/
└── .agent/
    └── rules/
        └── conventions.md
```

### Content
```markdown
# Project: [Name]

## Tech Stack
- Frontend: Next.js 14
- Backend: Express
- Database: PostgreSQL

## Conventions
- Components in `components/`
- API routes in `api/`
- Types in `types/`

## Database
- Use Prisma for ORM
- Always use transactions
- Include migrations
```

---

## Multiple Rule Files

Workspace can have multiple files:
```
.agent/rules/
├── conventions.md      # Code conventions
├── database.md         # Database rules
├── testing.md          # Testing requirements
└── security.md         # Security rules
```

All are loaded when working in this workspace.

---

## Token Considerations

Rules consume context tokens.

### Estimate
- ~4 characters = 1 token
- 500 words ≈ 375 tokens
- Keep GEMINI.md under 1000 words

### Optimization
- Use bullet points, not paragraphs
- Be concise but specific
- Remove outdated rules regularly

---

## Testing Rules

### Verify Rules Apply
```
You: Describe my code style preferences
Agent: [Should reflect your GEMINI.md rules]
```

### Check Specific Rule
```
You: What should you do before modifying files?
Agent: [Should mention your communication rules]
```
