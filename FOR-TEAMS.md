# Antigravity for Teams

Team adoption guide for engineering leaders.

---

## Why Teams Adopt Antigravity

| Before | After |
|--------|-------|
| Each engineer configures alone | Shared rules encode team standards |
| Knowledge leaves with people | Knowledge compounds in workflows |
| Inconsistent AI outputs | Standardized patterns team-wide |
| Manual verification | Automated artifact generation |
| One task at a time | Parallel agents, faster delivery |

---

## Three Rollout Options

### Option A: Self-Directed (Small Teams, <5 engineers)

**Investment**: 3 hours (course) + async practice

**Process**:
1. Each engineer completes the course independently
2. Slack channel for questions (#antigravity)
3. Weekly 30-min workflow sharing session

**Artifacts Produced**:
- [ ] Each engineer has GEMINI.md configured
- [ ] At least 1 shared workflow per engineer
- [ ] Team rules repository established

**When to Choose**: Self-motivated team. Already experimenting with AI tools.

---

### Option B: Cohort-Based (Medium Teams, 5-15 engineers)

**Investment**: 3 hours together + 2 weeks practice

**Process**:

**Day 1: Watch Together**
- Entire team watches course together
- Builds during pause points
- Immediate shared vocabulary

**Weeks 1-2: Practice Period**
| Day | Activity |
|-----|----------|
| 1-3 | Complete exercises 1-5 |
| 4-5 | Build one workflow for team use |
| 6-7 | Peer review workflows |
| 8-10 | Iterate based on feedback |
| 11-14 | Real workflow integration |

**Artifacts Produced**:
- [ ] Team GEMINI.md template
- [ ] 3-5 shared workflows
- [ ] Workspace rules for main projects
- [ ] Best practices documented

**When to Choose**: Dedicated learning time available. Coordination possible.

---

### Option C: Facilitated (Large Teams, 15+ engineers)

**Investment**: Custom engagement

**Process**:
1. **Discovery** - Understand team patterns and tech stack
2. **Custom Configuration** - Pre-built rules and workflows
3. **Training Session** - 3 hours + workshop
4. **Office Hours** - 2x 1-hour sessions for Q&A
5. **Repository Setup** - Turnkey team configuration

**Artifacts Produced**:
- [ ] Custom GEMINI.md for team standards
- [ ] Workflows matching team processes
- [ ] Configuration repository with CI/CD
- [ ] Champions trained (2-3 per team)

**When to Choose**: Faster time-to-value needed. Complex workflows.

**Contact**: [jai@pm-ai-lab.com](mailto:jai@pm-ai-lab.com)

---

## Team Configuration Repository

### Structure

```
team-antigravity/
├── README.md                      # How to use
├── SETUP.md                       # First-time setup
│
├── global/                        # Goes in ~/.gemini/
│   ├── GEMINI.md                  # Team global rules
│   └── workflows/                 # Team workflows
│       ├── standup.md
│       ├── pr-review.md
│       └── deploy.md
│
├── workspaces/                    # Templates
│   ├── frontend/
│   │   └── .agent/
│   └── backend/
│       └── .agent/
│
└── knowledge/                     # Importable entries
    ├── patterns/
    └── troubleshooting/
```

### Installation Script

```bash
#!/bin/bash
# setup-team-antigravity.sh

REPO="git@github.com:team/antigravity-config.git"
CONFIG_DIR="$HOME/.team-antigravity"

# Clone or update
if [ -d "$CONFIG_DIR" ]; then
    git -C "$CONFIG_DIR" pull
else
    git clone "$REPO" "$CONFIG_DIR"
fi

# Link global config
mkdir -p ~/.gemini/antigravity
ln -sf "$CONFIG_DIR/global/GEMINI.md" ~/.gemini/GEMINI.md
ln -sf "$CONFIG_DIR/global/workflows" ~/.gemini/antigravity/global_workflows

echo "Team configuration installed!"
```

---

## Champions Program

### Who Should Be Champions

- Completed this course
- Builds useful workflows
- Helps others troubleshoot
- Advocates for improvements

### Champion Responsibilities

| Weekly | Monthly |
|--------|---------|
| Answer questions | Review team config |
| Share workflows | Onboard new engineers |
| Collect feedback | Update documentation |

---

## Metrics to Track

### Leading Indicators (Week 1-4)

| Metric | Target | How to Measure |
|--------|--------|----------------|
| Setup completion | 100% | Checklist completion |
| First workflow created | 80%+ | Survey |
| GEMINI.md customized | 80%+ | File check |

### Lagging Indicators (Month 1-3)

| Metric | Target | How to Measure |
|--------|--------|----------------|
| Workflows shared | 3+ per engineer | Repo count |
| Parallel agent usage | 50%+ of complex tasks | Self-reported |
| Time savings | 20%+ | Survey |

---

## Common Objections

### "We already use Cursor/Copilot"

Antigravity isn't replacing your IDE tool. It's adding:
- Parallel agent orchestration
- Automated browser verification
- Persistent knowledge base
- Artifact-based trust

Many teams use multiple tools.

### "Too much configuration"

Start minimal:
1. Install Antigravity
2. Use team GEMINI.md
3. Learn one workflow

Add more as you see value.

### "Engineers will figure it out"

They'll learn Antigravity. They won't naturally:
- Create team standards
- Build shared workflows
- Establish verification patterns
- Document knowledge systematically

The course accelerates team value, not just individual productivity.

---

## ROI Calculation

### Conservative Estimates

| Factor | Estimate |
|--------|----------|
| Time saved per engineer | 30 min/day |
| Working days/month | 20 |
| Monthly hours saved | 10 hours |
| Fully-loaded hourly rate | $100 |
| Monthly savings per engineer | $1,000 |

### For 10-person team:
- **Monthly savings**: $10,000
- **Annual savings**: $120,000
- **Course investment**: 30 hours × $100 = $3,000
- **ROI**: 40x in year one

---

## Getting Started

### Option A
1. Share course link
2. Create #antigravity channel
3. Set 2-week deadline
4. Weekly sync meetings

### Option B
1. Schedule 4-hour block
2. Send setup instructions
3. Watch together
4. 2-week practice period

### Option C
Email [jai@pm-ai-lab.com](mailto:jai@pm-ai-lab.com) with:
- Team size
- Tech stack
- Current AI tool usage
- Specific pain points
