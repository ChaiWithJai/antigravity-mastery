# Pre-Course Setup

Complete these steps before starting the course.

**Estimated time: 10 minutes**

---

## Step 1: Download Antigravity

1. Go to [antigravity.google/download](https://antigravity.google/download)
2. Download for your OS:
   - macOS (Intel or Apple Silicon)
   - Windows
   - Linux

3. Run the installer

---

## Step 2: Initial Configuration

When you first launch Antigravity:

### 2a: Setup Flow

Choose one:
- **Fresh start** - Clean configuration
- **Import from VS Code** - Bring extensions and settings
- **Import from Cursor** - Bring Cursor configuration

### 2b: Theme Selection

Choose your preferred editor theme (can change later).

### 2c: Autonomy Level (Critical Decision)

| Level | Description | Recommended For |
|-------|-------------|-----------------|
| **Agent-driven** | Auto-executes commands and artifacts | Experienced users |
| **Agent-assisted** | Agent decides when to ask | **This course (recommended)** |
| **Review-driven** | Always asks before acting | Learning/sensitive projects |
| **Custom** | Fine-grained control | Advanced configuration |

**For this course**: Select **Agent-assisted**

### 2d: Terminal Policy

| Policy | Description | Recommended |
|--------|-------------|-------------|
| **Off** | Never auto-execute (except Allow list) | High security |
| **Auto** | Agent decides; asks for risky commands | **This course** |
| **Turbo** | Always auto-execute (except Deny list) | Speed over safety |

**For this course**: Select **Auto**

### 2e: Review Policy

| Policy | Description |
|--------|-------------|
| **Always Proceed** | Agent never asks for review |
| **Agent Decides** | Agent determines when review needed |
| **Request Review** | Agent always asks for review |

**For this course**: Select **Agent Decides**

---

## Step 3: Sign In

1. Click "Sign in with Google"
2. Use your personal Gmail account
3. This creates a new Chrome profile for agent browsing
4. Accept terms of use

---

## Step 4: Install Chrome Extension

The browser automation feature requires a Chrome extension:

1. In Antigravity, open Agent Manager (Cmd + E)
2. Select "Playground"
3. Type: "go to google.com"
4. When prompted, click "Setup"
5. Install the Antigravity Chrome extension
6. Grant permissions for browser automation

### Verify Installation

After setup, type in Agent Manager:
```
go to antigravity.google and take a screenshot
```

You should see:
- Browser opens automatically
- Agent navigates to the URL
- Screenshot artifact appears in chat

---

## Step 5: Create Test Workspace

1. Create a new folder: `~/antigravity-test`
2. In Antigravity, open this folder as a workspace
3. In Agent Manager, type: "create a hello world HTML file"
4. Verify agent creates the file

---

## Configuration Files Reference

After setup, these files are created:

| File | Location | Purpose |
|------|----------|---------|
| Global rules | `~/.gemini/GEMINI.md` | Rules for all projects |
| Browser allowlist | `~/.gemini/antigravity/browserAllowlist.txt` | Allowed URLs |
| Global workflows | `~/.gemini/antigravity/global_workflows/` | Reusable prompts |

Workspace-specific files (created per project):

| File | Location | Purpose |
|------|----------|---------|
| Workspace rules | `.agent/rules/` | Project-specific rules |
| Workspace workflows | `.agent/workflows/` | Project-specific prompts |

---

## Keyboard Shortcuts to Know

| Action | Mac | Windows/Linux |
|--------|-----|---------------|
| Toggle terminal | `Ctrl + `` ` | `Ctrl + `` ` |
| Toggle agent panel | `Cmd + L` | `Ctrl + L` |
| Inline completions | `Cmd + I` | `Ctrl + I` |
| Switch Editor/Manager | `Cmd + E` | `Ctrl + E` |

---

## Verification Checklist

Before starting the course, confirm:

- [ ] Antigravity installed and opens
- [ ] Signed in with Google account
- [ ] Chrome extension installed
- [ ] Test workspace created
- [ ] Agent can create files
- [ ] Agent can take screenshots

---

## Troubleshooting

### "Browser automation not working"

1. Check Chrome extension is installed
2. Verify URL is in allowlist (`~/.gemini/antigravity/browserAllowlist.txt`)
3. Restart Antigravity

### "Agent not executing commands"

1. Check Terminal Policy is "Auto" or "Turbo"
2. Verify command isn't in Deny list
3. Try adding command to Allow list

### "Can't sign in"

1. Check internet connection
2. Try different Google account
3. Clear Antigravity cache and restart

### "Agent taking too long"

1. Switch to "Fast" mode (instead of "Planning")
2. Simplify the request
3. Break into smaller tasks

---

## Ready to Start

Once all checkboxes are complete, proceed to:

**[Segment 0: Cold Open](./segments/00-cold-open.md)**

---

## Course Pause Points

During the course, you'll stop and practice at these moments:

| Pause | Time | What You Build |
|-------|------|----------------|
| 1 | 20m | GEMINI.md with global rules |
| 2 | 55m | Your first workflow |
| 3 | 85m | Multi-agent orchestration |
| 4 | 110m | Browser automation task |
| 5 | 150m | Knowledge base entry |

Each pause is 3-5 minutes. Instructions are in the `exercises/` folder.
