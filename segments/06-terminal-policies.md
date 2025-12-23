# Segment 6: Terminal Policies

**Duration: 15 minutes**

---

## Learning Objectives

By the end of this segment, you will:
- Configure terminal execution policies
- Create allow and deny lists
- Balance autonomy with safety

---

## The Autonomy Spectrum

```
Off                     Auto                     Turbo
│                         │                         │
▼                         ▼                         ▼
Never execute          Agent decides          Always execute
(ask for everything)   (smart judgment)       (except deny list)

←── More Safety                       More Speed ──→
```

---

## Terminal Policies

### Off (Maximum Safety)

Agent never auto-executes commands.

**Except**: Commands in your Allow List

**Use when**:
- Sensitive production access
- Learning a new codebase
- Training new team members

### Auto (Balanced) ← Recommended

Agent uses judgment:
- Safe commands execute automatically
- Risky commands prompt for approval

**Examples of auto-approved**:
- `npm install`
- `git status`
- `ls -la`

**Examples of prompted**:
- `rm -rf`
- `git push --force`
- `sudo anything`

### Turbo (Maximum Speed)

Agent always executes commands.

**Except**: Commands in your Deny List

**Use when**:
- Throwaway experiments
- Sandboxed environments
- Speed is critical

---

## Allow List (Off Policy)

When using **Off** policy, you need an Allow List of safe commands.

### Location
```
Settings → Advanced → Terminal → Allow List
```

### Example Allow List
```
ls
cat
npm install
npm run
git status
git diff
git log
npx
node
python
```

### Pattern Matching
```
npm *         # All npm commands
git status    # Only git status
git diff *    # git diff with any args
```

---

## Deny List (Turbo Policy)

When using **Turbo** policy, you need a Deny List of dangerous commands.

### Example Deny List
```
rm -rf
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

### Patterns to Block
```
rm -rf *      # Never recursive delete
*--force*     # Never force flags
sudo *        # Never sudo
*.env*        # Never touch env files
```

---

## Configuring Policies

### Via Settings

1. Cmd + ,  (Settings)
2. Search "Terminal"
3. Find "Execution Policy"
4. Select Off / Auto / Turbo

### Via GEMINI.md

```markdown
# Terminal Rules

## NEVER Auto-Execute
- Commands containing `rm -rf`
- Commands containing `--force`
- Commands starting with `sudo`
- Commands modifying `.env` files

## ALWAYS Safe to Execute
- `npm test`
- `npm run lint`
- `git status`
- `ls` variants
```

---

## Practical Configuration

### For Development

```
Policy: Auto

Allow (implicit):
- Build commands
- Test commands
- Dev server
- Git read operations

Deny (explicit):
- Force pushes
- Hard resets
- Recursive deletes
- Sudo commands
```

### For CI/CD Workflows

```
Policy: Off

Allow:
- npm ci
- npm run build
- npm test
- git push (specific branches)

Deny (everything else by default)
```

### For Learning/Experiments

```
Policy: Turbo

Deny:
- rm -rf
- sudo
- force flags
- production deployments
```

---

## Runtime Prompts

Even with Auto policy, agent will prompt for:

```
Agent: I need to run: npm run migrate:prod
       This affects production database.
       [Execute] [Modify] [Cancel]
```

### Options
- **Execute**: Run as-is
- **Modify**: Edit command before running
- **Cancel**: Don't run

---

## Context-Aware Safety

Agent considers:
- Command history (pattern of safe commands)
- File paths (production vs development)
- Keywords (delete, force, production)
- Time of day (unusual hours = extra caution)

---

## Anti-Patterns

### Too Restrictive
```
# Bad: Everything requires approval
Policy: Off
Allow List: (empty)
```
**Result**: Constant interruption, slow work.

### Too Permissive
```
# Bad: Everything auto-executes
Policy: Turbo
Deny List: (empty)
```
**Result**: One bad command = disaster.

### Inconsistent
```
# Bad: Allow dangerous commands
Policy: Off
Allow: rm -rf node_modules
```
**Result**: Risk from allowed dangerous commands.

---

## Recommended Setup

```markdown
# GEMINI.md Terminal Section

## Terminal Safety

### Never Auto-Execute (require confirmation)
- `rm -rf` or `rm -r`
- Any `--force` flag
- `sudo` commands
- Commands touching `.env` files
- `git push` to main/master
- `DROP` or `DELETE` SQL

### Safe to Auto-Execute
- `npm install`, `npm run *`, `npm test`
- `git status`, `git diff`, `git log`
- `ls`, `cat`, `head`, `tail`
- `node`, `python` (read-only scripts)
- Development server commands

### Ask Before
- `git push` to non-main branches
- Database migrations
- Deployment commands
```

---

## Checkpoint

You should now be able to:

- [ ] Explain the three terminal policies
- [ ] Configure allow and deny lists
- [ ] Write terminal rules in GEMINI.md
- [ ] Balance safety and speed

---

## Next

**[Segment 7: Knowledge Base →](./07-knowledge-base.md)**

Learn to teach agents patterns they can reuse.
