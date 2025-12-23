# Terminal Policies Reference

Quick reference for terminal execution settings.

---

## Policy Overview

| Policy | Auto-Execute | Prompts For |
|--------|--------------|-------------|
| **Off** | Only Allow List | Everything else |
| **Auto** | Safe commands | Risky commands |
| **Turbo** | Everything | Only Deny List |

---

## Off Policy

**Behavior**: Never auto-execute except Allow List

### Configure Allow List

Location: Settings → Advanced → Terminal → Allow List

### Example Allow List
```
ls
cat
npm install
npm run
npm test
git status
git diff
git log
npx
node
python
```

### Use When
- High-security environments
- Production access
- Learning/onboarding

---

## Auto Policy (Recommended)

**Behavior**: Agent decides based on risk

### Automatically Allowed
- Read-only commands (`ls`, `cat`, `git status`)
- Build commands (`npm run`, `make`)
- Package install (`npm install`)
- Dev servers (`npm run dev`)

### Prompts For
- Delete operations (`rm`)
- Force flags (`--force`)
- Sudo commands
- Unknown commands
- Commands matching deny patterns

### Use When
- General development
- Balanced safety/speed
- Most use cases

---

## Turbo Policy

**Behavior**: Always execute except Deny List

### Configure Deny List

Location: Settings → Advanced → Terminal → Deny List

### Example Deny List
```
rm -rf
rm -r
rmdir
sudo
curl | sh
wget | sh
eval
git push --force
git reset --hard
DROP TABLE
DELETE FROM
```

### Use When
- Isolated environments
- Throwaway projects
- Speed is critical

---

## Configuration via GEMINI.md

You can also specify in rules:

```markdown
# Terminal Safety

## NEVER Auto-Execute
- `rm -rf` or any recursive delete
- Commands with `--force`
- `sudo` commands
- Commands touching `.env` files
- `git push` to main/master
- Database DROP or DELETE

## ALWAYS Safe
- `npm install`, `npm run *`, `npm test`
- `git status`, `git diff`, `git log`
- `ls`, `cat`, `head`, `tail`
- Development server commands

## ASK Before
- `git push` to non-main branches
- Database migrations
- Deployment scripts
```

---

## Pattern Syntax

### Exact Match
```
rm -rf          # Only blocks "rm -rf"
```

### Wildcard
```
rm *            # Blocks any rm command
git push *      # Blocks any git push
*--force*       # Blocks anything with --force
```

### Prefix
```
sudo *          # Blocks sudo with any args
```

---

## Runtime Prompts

When agent needs approval:

```
Agent: I need to run: npm run migrate:prod
       This affects production database.

       [Execute] [Modify] [Cancel]
```

### Options
- **Execute**: Run as-is
- **Modify**: Edit command first
- **Cancel**: Don't run

---

## Common Patterns

### Development Setup
```
Policy: Auto

Safe by default:
- All npm commands
- All git read operations
- Dev servers

Prompt for:
- git push
- File deletion
```

### CI/CD Environment
```
Policy: Off

Allow List:
- npm ci
- npm run build
- npm test
- git push origin main
```

### Experimental
```
Policy: Turbo

Deny List:
- rm -rf
- sudo
- production deploy commands
```

---

## Troubleshooting

### "Command not executing"
1. Check current policy (Settings → Terminal)
2. If Off policy, add to Allow List
3. If Auto, may need approval

### "Dangerous command executed"
1. Review Deny List
2. Add pattern to block similar commands
3. Consider switching to Auto policy

### "Too many prompts"
1. Switch from Off to Auto
2. Or add common commands to Allow List
