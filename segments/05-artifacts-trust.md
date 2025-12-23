# Segment 5: Artifacts & Trust

**Duration: 20 minutes**

---

## Learning Objectives

By the end of this segment, you will:
- Understand the different artifact types
- Request specific artifacts for verification
- Build trust through verifiable work

---

## The Trust Problem

With traditional AI coding:
```
You: "Add user authentication"
AI: "Done! I've added authentication."
You: [Has it? Did it work? Are there bugs?]
```

**You hope. You don't know.**

---

## Artifacts: Proof of Work

Antigravity agents produce artifacts—verifiable deliverables that prove their work.

| Artifact | Purpose |
|----------|---------|
| Task List | What the agent planned |
| Implementation Plan | How it will be done |
| Code Diffs | What was actually changed |
| Screenshots | Visual proof of outcome |
| Recordings | Proof of interactive flows |
| Terminal Output | Proof of execution |

**Artifacts replace hope with evidence.**

---

## Artifact Types Deep Dive

### Task List

Generated before work begins:

```
📋 Task List

☑ 1. Create user model with email and password
☑ 2. Set up bcrypt for password hashing
☑ 3. Create registration endpoint
☐ 4. Create login endpoint
☐ 5. Add JWT token generation
☐ 6. Write tests for auth flows
```

**Value**: Shows the plan before execution. You can correct course early.

### Implementation Plan

Technical details of how:

```
📝 Implementation Plan

## Authentication Module

### User Model (`models/user.ts`)
- Define User interface with id, email, passwordHash
- Use Prisma for ORM
- Add unique constraint on email

### Password Handling (`utils/password.ts`)
- Use bcrypt with cost factor 12
- Separate hash and verify functions

### Endpoints (`routes/auth.ts`)
- POST /register: Create user, return JWT
- POST /login: Verify credentials, return JWT
- Tokens expire in 24 hours
```

**Value**: Review the approach before code is written.

### Code Diffs

What actually changed:

```
📄 Diff: models/user.ts

+ import { z } from 'zod';
+
+ export const UserSchema = z.object({
+   id: z.string().uuid(),
+   email: z.string().email(),
+   passwordHash: z.string(),
+   createdAt: z.date(),
+ });
+
+ export type User = z.infer<typeof UserSchema>;
```

**Value**: Review exact changes before accepting.

### Screenshots

Visual proof:

```
📸 Screenshot: Registration Form

[Image showing the registration form with email and password fields]

📸 Screenshot: Successful Registration

[Image showing success message after registration]
```

**Value**: See the outcome without running the code yourself.

### Recordings

Interactive flow proof:

```
🎬 Recording: Login Flow (0:32)

Shows:
- User enters credentials
- Clicks login button
- Redirects to dashboard
- Shows welcome message
```

**Value**: Verify interactive behavior.

---

## Requesting Artifacts

### Implicit Request

Some artifacts are automatic:
- Task list (before complex tasks)
- Implementation plan (for multi-step work)
- Code diffs (for changes)

### Explicit Request

Ask for specific artifacts:

```
"After implementing the feature, take a screenshot showing it works"

"Record a walkthrough of the entire user flow"

"Show me the code diff before applying changes"

"Generate a summary of all changes made"
```

---

## Reviewing Artifacts

### Task List Review

Before work begins:
```
Agent: Here's my task list for this feature...

You: "Add a step for error handling. Also, move testing earlier in the list."

Agent: Updated task list:
       1. [Updated based on feedback]
```

### Implementation Plan Review

Check the approach:
```
Agent: Here's my implementation plan...

You: "Use argon2 instead of bcrypt. Also, tokens should expire in 1 hour, not 24."

Agent: Updating plan...
```

### Code Diff Review

Before accepting:
```
Agent: Here are the changes I made...

You: "The error message is too generic. Make it more specific."

Agent: Updating code...
```

---

## Artifact Feedback

You can comment on artifacts like Google Docs:

1. Hover over artifact section
2. Click comment icon
3. Add your feedback
4. Agent receives and addresses comments

**This is collaborative refinement, not just review.**

---

## Undo Capability

If something went wrong:

1. Find the point in conversation where things were good
2. Click the undo icon (↩️)
3. "Undo changes up to this point"
4. Agent reverts to that state

**Artifacts + undo = safe experimentation.**

---

## Trust Hierarchy

```
Low Trust                                           High Trust
─────────────────────────────────────────────────────────────
Raw Output    Task List    Plan    Diff    Screenshot    Recording
              ────────────────────────────────────────────────────→
              More artifacts = more trust
```

For high-stakes work, request more artifacts.

---

## Practical Pattern

### Standard Feature Request

```
You: Build a comment system with:
     - Add/delete comments
     - Reply to comments
     - Likes on comments

     Before starting, show me the task list.
     Before coding, show me the implementation plan.
     After coding, show me the diff.
     After testing, show me screenshots.
```

Agent produces 4 layers of verification.

---

## When to Request More Artifacts

**Request more when:**
- High-stakes changes (auth, payments, data)
- Complex features
- Learning the codebase
- Before important releases

**Request less when:**
- Simple changes
- Well-understood patterns
- Tight iteration loops
- Throwaway experiments

---

## Checkpoint

You should now understand:

- [ ] What each artifact type shows
- [ ] How to request specific artifacts
- [ ] How to review and provide feedback
- [ ] When to request more vs less verification

---

## Next

**[Segment 6: Terminal Policies →](./06-terminal-policies.md)**

Learn to configure safety boundaries for agent execution.
