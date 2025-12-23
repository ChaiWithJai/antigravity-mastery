# Exercise 3: Multi-Agent Orchestration

**Duration: 5 minutes**

---

## Objective

Spawn two agents to work on related tasks in parallel.

---

## Steps

### Step 1: Identify two related but independent tasks

Examples:
- Backend API + Frontend UI
- Feature implementation + Tests
- Documentation + Code examples
- Bug fix + Regression tests

### Step 2: Open Agent Manager

Press Cmd + E to toggle to Agent Manager view.

### Step 3: Start first agent

1. Click "Start Conversation" (or `+`)
2. Select your workspace
3. Give the first task:
   ```
   Build a REST API endpoint for user profiles.
   Include GET and PUT operations.
   ```

### Step 4: Start second agent

1. Click "Start Conversation" again
2. Select appropriate workspace (can be same or different)
3. Give the second task:
   ```
   Create a user profile UI component.
   Include fields for name, email, and avatar.
   ```

### Step 5: Monitor both

Watch the Inbox:
- Both should show active status
- Review artifacts as they're produced
- Answer questions if agent asks

### Step 6: Coordinate if needed

When one finishes, you may need to share context:
```
You (to Agent 2): The API is done.
The endpoints are:
- GET /api/users/:id
- PUT /api/users/:id
Update the UI to use these.
```

---

## Success Criteria

- [ ] Two agents running simultaneously
- [ ] Both producing artifacts
- [ ] You can switch between conversations
- [ ] Tasks complete independently

---

## Tips

- Keep tasks truly independent initially
- Start simple (2 agents) before scaling up
- Use the Inbox to track status at a glance
- You are the coordinator between agents

---

## Example Scenario

See [solution/scenario.md](./solution/scenario.md) for a complete example.
