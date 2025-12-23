# Global Rules

## Code Style

### Languages
- Use TypeScript for all JavaScript projects
- Use Python 3.11+ with type hints
- Prefer functional patterns over classes when practical

### Formatting
- Use Prettier defaults for JS/TS
- Use Black for Python
- 2 spaces for indentation (JS/TS), 4 spaces (Python)

### Best Practices
- Always include error handling for async operations
- Prefer `async/await` over Promise chains
- Write self-documenting code; add comments only for "why", not "what"

---

## Safety

### NEVER Auto-Execute
- Commands containing `rm -rf` or recursive delete
- Commands with `--force` flags
- Any `sudo` commands
- Commands that modify `.env` files
- Deployment commands to production

### ALWAYS Confirm Before
- Database migrations
- Git pushes to main/master
- File deletions
- Package major version upgrades

### Secrets
- Never commit secrets or API keys
- Use environment variables
- Alert immediately if credentials detected in code

---

## Communication

### Before Starting
- State what you're about to do in plain language
- List files you'll create or modify
- Ask for clarification if requirements are ambiguous

### During Work
- Provide progress updates for tasks over 30 seconds
- Explain any unexpected issues encountered
- Ask before deviating from the plan

### After Completing
- Summarize what was done
- List any follow-up actions needed
- Note any concerns or recommendations

---

## Testing

- Write tests for new functions
- Run existing tests before marking task complete
- If tests fail, fix before proceeding
- Aim for meaningful coverage, not 100% for the sake of it
