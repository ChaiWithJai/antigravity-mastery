# Team Global Rules

This file goes in `~/.gemini/GEMINI.md` for all team members.

---

## Code Standards

### Languages
- TypeScript for all frontend and backend JavaScript
- Python 3.11+ with type hints
- Go for microservices

### Formatting
- Prettier for JS/TS (use project config)
- Black for Python
- gofmt for Go
- Run formatters before committing

### Patterns
- Prefer functional patterns over classes (when practical)
- Use async/await, never raw Promises
- Always handle errors explicitly
- No console.log in production code (use proper logging)

---

## Git Practices

### Branch Naming
```
feature/[ticket-id]-[short-description]
fix/[ticket-id]-[short-description]
chore/[short-description]
```

### Commits
- Conventional commits format: `type(scope): description`
- Types: feat, fix, docs, style, refactor, test, chore
- One logical change per commit
- No "WIP" or "fix typo" commits on main

### Pull Requests
- Description required (use template)
- Screenshots for UI changes
- Link to ticket/issue
- Get at least one review before merge

---

## Safety

### NEVER Auto-Execute
- Commands with `rm -rf`
- Commands with `--force`
- `sudo` anything
- Commands affecting `.env` files
- Database DROP or DELETE without WHERE
- Deployments to production

### ALWAYS Confirm Before
- Git push to main/master
- Database migrations
- File deletions
- Major version upgrades
- External API integrations

### Secrets
- Never commit secrets or API keys
- Use environment variables
- If you accidentally commit a secret, rotate it immediately
- Report security concerns to #security channel

---

## Communication

### Before Starting Complex Tasks
- State what you're about to do
- List files you'll modify
- Get confirmation if requirements unclear

### During Work
- Provide progress updates for long tasks
- Explain unexpected issues
- Ask before deviating from plan

### After Completing
- Summarize what was done
- List any follow-up needed
- Note concerns or technical debt

---

## Testing

- Write tests for new functions
- Run tests before marking complete
- If tests fail, fix before proceeding
- Include edge cases
- Mock external services

---

## Documentation

- Update README when adding features
- Document non-obvious code with comments (why, not what)
- Keep API docs in sync
- Update changelogs for user-facing changes
