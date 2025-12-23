# Segment 3: Agent Manager

**Duration: 30 minutes**

---

## Learning Objectives

By the end of this segment, you will:
- Navigate the Agent Manager interface
- Spawn multiple agents on related tasks
- Understand when parallel vs sequential work

---

## The Two Views

### Editor View
- Traditional IDE
- Synchronous work
- Agent panel on side
- **For**: Hands-on coding, quick questions

### Agent Manager
- Mission control
- Asynchronous orchestration
- Multiple agents visible
- **For**: Complex tasks, parallel work

**Toggle with Cmd + E**

---

## Agent Manager Anatomy

```
┌─────────────────────────────────────────────────────────────────┐
│ Antigravity                                              [─ □ ×]│
├────────────────┬────────────────────────────────────────────────┤
│                │                                                │
│  📥 Inbox      │   Conversation                                 │
│                │                                                │
│  ➕ Start      │   You: Build a REST API for users             │
│                │                                                │
│  📁 Workspaces │   Agent: I'll create a task list...           │
│    └─ project1 │                                                │
│    └─ project2 │   📋 Task List                                │
│                │   ☑ Set up Express server                     │
│  🎮 Playground │   ☑ Create user model                         │
│                │   ☐ Implement CRUD routes                     │
│  📝 Editor     │   ☐ Add authentication                        │
│                │                                                │
│  🌐 Browser    │   📝 Implementation Plan                      │
│                │   [Detailed technical plan...]                 │
│                │                                                │
│  💾 Knowledge  │   💬 [Input field]                            │
│                │                                                │
└────────────────┴────────────────────────────────────────────────┘
```

---

## Core Concepts

### Inbox
All your conversations. Like email inbox for agent chats.

### Workspaces
Folders/projects the agent can work in. Each workspace is isolated.

### Playground
Scratch space for experiments. No persistent workspace.

### Browser
Agent-controlled Chrome. For verification and web tasks.

### Knowledge Base
Saved context agents can reference in future conversations.

---

## Spawning Multiple Agents

### Why Multiple Agents?

| Single Agent | Multiple Agents |
|--------------|-----------------|
| Sequential work | Parallel work |
| One context | Separate contexts |
| Blocks on each step | Independent progress |
| Simpler | More complex, faster |

### How to Spawn

**Method 1: New Conversation**
1. Click "Start Conversation" (or `+`)
2. Select workspace
3. Give task
4. Repeat for another task

**Method 2: From Existing**
```
You: Start a new agent to work on the frontend while you continue the backend
Agent: [Spawns new conversation, continues current work]
```

---

## Parallel Work Patterns

### Pattern 1: Frontend + Backend

```
Agent 1: "Build the REST API for users"
         Workspace: backend/

Agent 2: "Build the user management UI"
         Workspace: frontend/
```

Both work simultaneously. You review both when done.

### Pattern 2: Feature + Tests

```
Agent 1: "Implement the payment processing module"
         Workspace: src/

Agent 2: "Write comprehensive tests for payment processing"
         Workspace: tests/
```

Agent 2 can start with test stubs while Agent 1 builds.

### Pattern 3: Research + Implementation

```
Agent 1: "Research best practices for caching in Node.js"
         Workspace: (any)

Agent 2: "Implement basic caching using what's already in our codebase"
         Workspace: project/
```

Agent 1 goes deep on research. Agent 2 uses existing patterns.

---

## Managing Multiple Agents

### Inbox View

Each conversation shows:
- Last message preview
- Workspace name
- Status (working, waiting, done)

### Switching Context

Click conversation in Inbox to switch focus.

### Waiting for Review

When agent needs approval, you'll see it in Inbox.

---

## When to Use Multiple Agents

**Use Multiple When:**
- Tasks are independent
- Different parts of codebase
- Want faster completion
- Exploring multiple approaches

**Use Single When:**
- Tasks depend on each other
- Need sequential logic
- Simpler oversight
- Learning/debugging

---

## Agent Coordination

Agents don't directly communicate. You coordinate:

```
Agent 1: [Finishes API]
You: "The API is done. Here's the endpoint structure: [paste]"
Agent 2: "Got it, updating the frontend to use these endpoints..."
```

**You are the message bus between agents.**

---

## Practical Example

### Task: Build a Blog Platform

**Agent 1: Backend**
```
Build a blog API with:
- Post CRUD operations
- User authentication
- Comment system
Use Express and PostgreSQL.
```

**Agent 2: Frontend**
```
Build a blog frontend with:
- Post listing page
- Post detail view
- Markdown editor
Use Next.js and Tailwind.
```

**Agent 3: DevOps**
```
Set up deployment:
- Docker configuration
- GitHub Actions CI/CD
- Staging and production environments
```

Three agents, working in parallel, different concerns.

---

## Monitoring Progress

### Artifacts in Each Conversation

Each agent produces artifacts:
- Task lists (what they're doing)
- Implementation plans (how)
- Screenshots (proof)

### Quick Status Check

Scan Inbox:
- Active conversations show typing indicator
- Waiting conversations need your input
- Completed conversations show done state

---

## Pause Point #3

**Time to practice: 5 minutes**

Go to [exercises/03-agent-manager/](../exercises/03-agent-manager/) and spawn 2 agents on related tasks.

---

## Checkpoint

You should now be able to:

- [ ] Navigate Agent Manager interface
- [ ] Spawn multiple agents in parallel
- [ ] Know when parallel work makes sense
- [ ] Coordinate between agents

---

## Next

**[Segment 4: Browser Automation →](./04-browser-automation.md)**

Learn to set up agents that verify their own work.
