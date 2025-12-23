# Segment 8: Production Setup

**Duration: 15 minutes**

---

## Learning Objectives

By the end of this segment, you will:
- Verify your complete Antigravity setup
- Know where all configuration files live
- Have a production-ready environment

---

## Configuration File Map

```
~/.gemini/
├── GEMINI.md                              # Global rules
└── antigravity/
    ├── browserAllowlist.txt               # Allowed URLs
    └── global_workflows/                  # Global workflows
        ├── standup.md
        └── deploy.md

[workspace]/
└── .agent/
    ├── rules/                             # Workspace rules
    │   └── project-conventions.md
    └── workflows/                         # Workspace workflows
        ├── test.md
        └── build.md
```

---

## Verification Checklist

### 1. Global Setup

**GEMINI.md exists and has content:**
```bash
cat ~/.gemini/GEMINI.md
```

Should contain:
- [ ] Code style preferences
- [ ] Safety constraints
- [ ] Communication preferences

**Browser allowlist configured:**
```bash
cat ~/.gemini/antigravity/browserAllowlist.txt
```

Should contain:
- [ ] localhost entries
- [ ] Development URLs
- [ ] Internal tools

**At least one global workflow:**
```bash
ls ~/.gemini/antigravity/global_workflows/
```

Should have at least one `.md` file.

---

### 2. Terminal Policies

**Check current policy:**

Settings → Terminal → Execution Policy

Should be:
- [ ] Auto (recommended) or
- [ ] Off with Allow List configured

**Deny list configured (if Turbo):**

Should block:
- [ ] `rm -rf`
- [ ] `sudo`
- [ ] Force flags

---

### 3. Browser Automation

**Test browser capability:**
```
Agent Manager > "Go to localhost:3000 and take a screenshot"
```

Should:
- [ ] Open Chrome
- [ ] Navigate successfully
- [ ] Produce screenshot artifact

---

### 4. Knowledge Base

**Has at least one entry:**

Agent Manager → Knowledge (Cmd + K)

Should have:
- [ ] At least one saved entry
- [ ] Proper tags
- [ ] Descriptive title

---

### 5. Workspace Configuration

For your main project:

**.agent/rules/ exists:**
```bash
ls [workspace]/.agent/rules/
```

Should have project-specific rules.

**.agent/workflows/ exists (optional):**
```bash
ls [workspace]/.agent/workflows/
```

Project-specific workflows if needed.

---

## Complete Setup Summary

```
┌─────────────────────────────────────────────────────────────────┐
│                     PRODUCTION SETUP                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  GLOBAL (~/.gemini/)                                           │
│  ├─ GEMINI.md              ✓ Style, Safety, Communication     │
│  ├─ browserAllowlist.txt   ✓ Allowed URLs                     │
│  └─ global_workflows/      ✓ At least 1 workflow              │
│                                                                 │
│  SETTINGS                                                       │
│  ├─ Terminal Policy        ✓ Auto (or Off + Allow List)       │
│  ├─ Review Policy          ✓ Agent Decides                    │
│  └─ Chrome Extension       ✓ Installed and working            │
│                                                                 │
│  KNOWLEDGE BASE                                                 │
│  └─ Entries                ✓ At least 1 saved pattern         │
│                                                                 │
│  WORKSPACE ([project]/.agent/)                                 │
│  ├─ rules/                 ✓ Project conventions              │
│  └─ workflows/             ○ Optional project workflows       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Common Gaps

### Gap 1: Empty GEMINI.md

**Fix**: Add at minimum:
```markdown
# Global Rules

## Code Style
- Use TypeScript for JavaScript projects
- Include error handling

## Safety
- Never run destructive commands without confirmation
```

### Gap 2: No Browser Allowlist

**Fix**: Add development URLs:
```
localhost
localhost:*
127.0.0.1
```

### Gap 3: No Knowledge Entries

**Fix**: Save one pattern you use often. Even:
```markdown
# Git Commit Format

format: type(scope): description

types: feat, fix, docs, style, refactor, test, chore
```

### Gap 4: No Workspace Rules

**Fix**: Create `.agent/rules/conventions.md`:
```markdown
# Project Conventions

- Use [your framework]
- Follow [your patterns]
- Test before committing
```

---

## Maintenance Schedule

### Weekly
- Review and clear old conversations
- Update knowledge base with new learnings
- Check for Antigravity updates

### Monthly
- Review GEMINI.md rules (still relevant?)
- Audit workflows (still accurate?)
- Clean knowledge base (outdated entries?)

### Quarterly
- Full setup verification (this checklist)
- Performance review (what's working?)
- Policy adjustment (too restrictive? too loose?)

---

## Export Configuration

For backup or team sharing:

```bash
# Create backup
mkdir -p ~/antigravity-backup
cp -r ~/.gemini ~/antigravity-backup/
cp -r [workspace]/.agent ~/antigravity-backup/workspace-agent/

# Create tarball
tar -czf antigravity-config.tar.gz ~/antigravity-backup/
```

---

## Checkpoint

Your setup is production-ready when:

- [ ] GEMINI.md has meaningful rules
- [ ] Terminal policy matches your risk tolerance
- [ ] Browser automation works
- [ ] Knowledge base has entries
- [ ] Main workspace has rules
- [ ] You can trigger a global workflow

---

## Next

**[Segment 9: Team Patterns →](./09-team-patterns.md)**

Learn to share your setup with your team.
