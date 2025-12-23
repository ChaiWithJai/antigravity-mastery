# Artifact Types Reference

Quick reference for Antigravity artifacts.

---

## Artifact Overview

| Artifact | When Created | Purpose |
|----------|--------------|---------|
| Task List | Before complex work | Shows planned steps |
| Implementation Plan | Before coding | Technical approach |
| Code Diff | After code changes | Shows exact changes |
| Screenshot | On request or verification | Visual proof |
| Recording | On request | Interactive flow proof |
| Terminal Output | After commands | Execution proof |

---

## Task List

### When Created
- Automatically for multi-step tasks
- When you ask "what's the plan?"

### Format
```
📋 Task List

☑ 1. Completed step
☑ 2. Another completed step
☐ 3. Pending step
☐ 4. Future step
```

### How to Use
- Review before agent starts
- Suggest additions or reordering
- Tracks progress during execution

### Request It
```
Before starting, show me the task list.
What steps will you take?
```

---

## Implementation Plan

### When Created
- For complex technical tasks
- When architecture decisions needed

### Format
```
📝 Implementation Plan

## Component: [Name]

### Approach
[Technical description]

### Files to Create/Modify
- path/to/file.ts
- path/to/another.ts

### Dependencies
- Required packages
- Prerequisites

### Considerations
- Trade-offs
- Risks
```

### How to Use
- Review approach before coding
- Suggest alternative approaches
- Approve or request changes

### Request It
```
Show me the implementation plan before coding.
How will you approach this?
```

---

## Code Diff

### When Created
- After any code changes
- Before applying changes (in review mode)

### Format
```
📄 Diff: path/to/file.ts

- removed line
+ added line
  unchanged line
```

### How to Use
- Review exact changes
- Request modifications
- Accept or reject

### Request It
```
Show me the diff before applying changes.
What exactly changed?
```

---

## Screenshot

### When Created
- On explicit request
- During browser automation
- For verification

### Format
```
📸 Screenshot: description.png

[Visual image of the current state]
```

### How to Use
- Verify UI changes
- Document current state
- Prove functionality works

### Request It
```
Take a screenshot of the result.
Show me what it looks like.
Screenshot the error message.
```

---

## Recording

### When Created
- On explicit request
- For interactive flow verification

### Format
```
🎬 Recording: flow-name.mp4 (0:32)

[Video recording of browser interaction]

Shows:
1. Step one
2. Step two
3. Step three
```

### How to Use
- Verify complex user flows
- Document processes
- Prove end-to-end functionality

### Request It
```
Record a walkthrough of the checkout flow.
Show me a video of the login process.
```

---

## Terminal Output

### When Created
- After command execution
- With test results
- With build output

### Format
```
💻 Terminal Output

$ npm test
> Running tests...
✓ Test 1 passed
✓ Test 2 passed
2 tests passed
```

### How to Use
- Verify command success
- Debug failures
- Confirm execution

### Request It
```
Show me the full terminal output.
What did the command return?
```

---

## Artifact Best Practices

### For High-Stakes Work
Request multiple artifacts:
```
Before starting, show me the task list.
Then the implementation plan.
After changes, show the diff.
Finally, take a screenshot proving it works.
```

### For Quick Iteration
Minimize artifacts:
```
Just make the change, I'll review in code.
```

### For Documentation
Save artifacts:
```
Save this implementation plan to the knowledge base.
Export these screenshots for the README.
```

---

## Troubleshooting

### "No artifacts appearing"
- Agent may be in fast mode (less artifacts)
- Explicitly request: "Generate a task list first"

### "Screenshot is blank"
- Page may not have loaded
- Request: "Wait for page to load, then screenshot"

### "Recording not working"
- Check Chrome extension
- Check URL is in allowlist
