# Exercise 5: Knowledge Base Entry

**Duration: 3 minutes**

---

## Objective

Create a knowledge base entry for a pattern or solution you use often.

---

## Steps

### Step 1: Identify something worth saving

Think of:
- A tricky bug solution you've found
- A code pattern you use repeatedly
- A configuration that took time to figure out
- A process you follow

### Step 2: Open Knowledge Base

- In Agent Manager, click "Knowledge" in sidebar
- Or press Cmd + K

### Step 3: Create a new entry

Click "Add Entry" and fill in:

**Title**: Clear, searchable name
```
Example: "CORS Configuration for Express"
```

**Content**: Include context and solution
```markdown
## Problem
API requests from frontend blocked by CORS.

## Solution
```javascript
const cors = require('cors');

app.use(cors({
  origin: process.env.FRONTEND_URL,
  credentials: true
}));
```

## Notes
- For development, can use `origin: '*'`
- For production, always specify exact origin
- credentials: true needed for cookies
```

**Tags**: Relevant categories
```
#cors #express #backend #api
```

### Step 4: Verify it saves

Search for your entry by keyword.

### Step 5: Test reference

In a new conversation:
```
What do I have saved about [your topic]?
```

Agent should find and reference your entry.

---

## Success Criteria

- [ ] Knowledge entry created
- [ ] Has descriptive title
- [ ] Has helpful content with context
- [ ] Has relevant tags
- [ ] Can be found via search

---

## Good Knowledge Entry Patterns

### Bug Solution
```markdown
# [Error Message]

## When You See This
[Context where error appears]

## Cause
[Why it happens]

## Fix
[Solution with code]

## Prevention
[How to avoid in future]
```

### Code Pattern
```markdown
# [Pattern Name]

## Use When
[When to use this pattern]

## Implementation
[Code example]

## Trade-offs
[Pros and cons]

## Examples
[Real usage examples]
```

### Configuration
```markdown
# [Tool/System] Configuration

## Purpose
[What this configures]

## Setup
[Step by step]

## Common Options
[Key settings explained]

## Troubleshooting
[Common issues]
```

---

## Example

See [solution/entry.md](./solution/entry.md) for a complete example.
