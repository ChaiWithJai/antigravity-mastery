# Segment 9: Team Patterns

**Duration: 25 minutes**

---

## Learning Objectives

By the end of this segment, you will:
- Create shareable rules and workflows
- Set up a team configuration repository
- Know the team adoption playbook

---

## What to Share

| Asset | Individual | Team |
|-------|------------|------|
| GEMINI.md | Personal preferences | Team standards |
| Workflows | Your shortcuts | Team processes |
| Rules | Your style | Team conventions |
| Knowledge | Your notes | Team documentation |

---

## Team Configuration Repository

### Structure

```
team-antigravity/
├── README.md                      # How to use this repo
├── SETUP.md                       # First-time setup
│
├── global/                        # Goes in ~/.gemini/
│   ├── GEMINI.md                  # Team global rules
│   └── workflows/                 # Team global workflows
│       ├── standup.md
│       ├── pr-review.md
│       └── deploy.md
│
├── workspaces/                    # Templates for projects
│   ├── frontend/
│   │   └── .agent/
│   │       ├── rules/
│   │       └── workflows/
│   ├── backend/
│   │   └── .agent/
│   └── fullstack/
│       └── .agent/
│
├── knowledge/                     # Importable knowledge entries
│   ├── patterns/
│   ├── conventions/
│   └── troubleshooting/
│
└── onboarding/                    # New engineer guide
    ├── first-day.md
    └── exercises/
```

---

## Team GEMINI.md

Shared rules that apply to everyone:

```markdown
# Team Global Rules

## Code Standards

### Language Preferences
- TypeScript for all frontend/backend JavaScript
- Python 3.11+ for data pipelines
- Go for microservices

### Style
- Use Prettier for formatting (don't argue with it)
- ESLint with team config
- No console.log in production code

## Pull Request Standards

### Before Creating PR
- All tests pass locally
- No linting errors
- Changes are rebased on main

### PR Description
- Summary of what and why
- Screenshots for UI changes
- Testing notes

## Git Practices

### Branch Naming
- feature/[ticket]-[description]
- fix/[ticket]-[description]
- chore/[description]

### Commits
- Conventional commits format
- One logical change per commit
- No "WIP" commits on main

## Security

### NEVER Auto-Execute
- Commands affecting production
- Database drops or deletes
- Credential handling

### Secrets
- Never commit secrets
- Use environment variables
- Report any secret exposure immediately

## Communication

- Explain before complex operations
- Ask for clarification if requirements unclear
- Tag @human when blocked
```

---

## Team Workflows

### PR Review Workflow

```markdown
# pr-review.md

## Team PR Review Process

When reviewing a PR:

### 1. Context
- Read the PR description
- Understand the ticket/issue being addressed

### 2. Automated Checks
- Verify CI is passing
- Check test coverage change
- Review linting results

### 3. Code Review
For each file:
- Does it follow team conventions?
- Are there security concerns?
- Is error handling appropriate?
- Is it tested adequately?

### 4. Output Format

**Overall Assessment**
[Approve / Request Changes / Comment]

**Summary**
[1-2 sentences on the change]

**Issues (if any)**
- [ ] [Blocking issue requiring change]
- [ ] [Blocking issue requiring change]

**Suggestions (non-blocking)**
- [Optional improvement]
- [Optional improvement]

**Questions**
- [Clarification needed]
```

### Deploy Workflow

```markdown
# deploy.md

## Team Deployment Process

### Pre-Deploy
1. Verify all tests pass on main
2. Check no blocking PRs
3. Confirm deployment window

### Staging Deploy
1. Deploy to staging: [team command]
2. Run smoke tests
3. Verify key flows work
4. Get QA signoff (if applicable)

### Production Deploy
1. Announce in #deployments
2. Deploy to production: [team command]
3. Monitor error rates for 15 minutes
4. Verify key metrics stable

### Rollback (if needed)
1. Announce issue in #deployments
2. Rollback: [team command]
3. Verify rollback successful
4. Create incident report
```

---

## Sharing Configuration

### Option 1: Git Repository

```bash
# Clone team config
git clone git@github.com:team/antigravity-config.git

# Link global config
ln -sf ~/antigravity-config/global/GEMINI.md ~/.gemini/GEMINI.md
ln -sf ~/antigravity-config/global/workflows ~/.gemini/antigravity/global_workflows

# Copy workspace config (for new projects)
cp -r ~/antigravity-config/workspaces/frontend/.agent ./
```

### Option 2: Script Setup

```bash
#!/bin/bash
# setup-team-antigravity.sh

TEAM_REPO="git@github.com:team/antigravity-config.git"
CONFIG_DIR="$HOME/.team-antigravity"

echo "Setting up team Antigravity configuration..."

# Clone or update
if [ -d "$CONFIG_DIR" ]; then
    git -C "$CONFIG_DIR" pull
else
    git clone "$TEAM_REPO" "$CONFIG_DIR"
fi

# Link global rules
mkdir -p ~/.gemini/antigravity
ln -sf "$CONFIG_DIR/global/GEMINI.md" ~/.gemini/GEMINI.md
ln -sf "$CONFIG_DIR/global/workflows" ~/.gemini/antigravity/global_workflows

echo "Team configuration installed!"
```

---

## Onboarding New Engineers

### First Day Checklist

```markdown
# New Engineer Antigravity Setup

## 1. Install Antigravity
- Download from antigravity.google/download
- Run installer
- Sign in with Google account

## 2. Install Team Configuration
```bash
./setup-team-antigravity.sh
```

## 3. Configure Personal Preferences
Add your personal preferences AFTER team rules in GEMINI.md:
```markdown
# Personal Preferences (below team rules)
- [Your specific preferences]
```

## 4. Verify Setup
- [ ] GEMINI.md has team rules
- [ ] `/standup` workflow works
- [ ] `/pr-review` workflow works

## 5. Complete Training
Work through the [Antigravity Mastery](link) course exercises.
```

---

## Champions Program

### Who Should Be a Champion

- Engineers who completed this course
- Those who build useful workflows
- People who help others troubleshoot

### Champion Responsibilities

| Weekly | Monthly |
|--------|---------|
| Answer questions | Review team GEMINI.md |
| Share useful workflows | Onboard new engineers |
| Collect improvement ideas | Update documentation |

---

## Measuring Adoption

### Leading Indicators (Week 1-4)

| Metric | Target | How |
|--------|--------|-----|
| Setup completion | 100% | Track checklist completion |
| First workflow used | 80%+ | Survey |
| GEMINI.md customized | 80%+ | Check file modification |

### Lagging Indicators (Month 1-3)

| Metric | Target | How |
|--------|--------|-----|
| Workflows created | 3+ per engineer | Count in repo |
| Knowledge entries | 5+ per engineer | KB stats |
| Time savings | 20%+ | Self-reported |

---

## Handling Resistance

### "I prefer my current setup"

Antigravity doesn't replace your editor. It adds:
- Parallel agent work
- Browser automation
- Persistent knowledge

You can use both.

### "This is too much configuration"

Start with team defaults. Customize over time.

Minimum setup:
1. Team GEMINI.md
2. One workflow

### "I don't trust AI execution"

Use:
- Terminal Policy: Off
- Review Policy: Always Review
- Artifact requirements: Maximum

Build trust gradually.

---

## Checkpoint

Your team setup is complete when:

- [ ] Team config repository exists
- [ ] GEMINI.md has team standards
- [ ] Core workflows are defined
- [ ] Onboarding doc is written
- [ ] Champions identified

---

## Course Complete

You've finished Antigravity Mastery.

**What you built:**
1. GEMINI.md with global rules
2. Custom workflows with `/trigger`
3. Multi-agent orchestration skills
4. Browser automation setup
5. Knowledge base entries
6. Production configuration
7. Team adoption plan

**Next steps:**
1. Complete [FOR-TEAMS.md](../FOR-TEAMS.md) if you're leading adoption
2. Get your [certificate](../COMPLETION.md)
3. Share what you learned with your team

---

**[← Back to README](../README.md)** | **[Get Certificate →](../COMPLETION.md)**
