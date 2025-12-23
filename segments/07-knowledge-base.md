# Segment 7: Knowledge Base

**Duration: 20 minutes**

---

## Learning Objectives

By the end of this segment, you will:
- Save useful context to the knowledge base
- Reference knowledge in future conversations
- Build institutional memory for your agents

---

## What is the Knowledge Base?

The Knowledge Base is persistent storage for context agents can reference.

```
Traditional AI:
Conversation 1 → [forgotten]
Conversation 2 → [starts fresh]
Conversation 3 → [no memory]

With Knowledge Base:
Conversation 1 → Save to KB
Conversation 2 → Reference KB
Conversation 3 → Reference KB + Add more
```

**Knowledge compounds across sessions.**

---

## Accessing Knowledge Base

In Agent Manager:
1. Click "Knowledge" in sidebar
2. Or use Cmd + K

### Views
- **List**: All saved knowledge entries
- **Search**: Find specific entries
- **Tags**: Filter by category

---

## What to Save

### Code Snippets

```markdown
# Authentication Pattern

Use this pattern for JWT auth:

\`\`\`typescript
const verifyToken = (token: string) => {
  try {
    return jwt.verify(token, process.env.JWT_SECRET);
  } catch {
    return null;
  }
};
\`\`\`

Always use try/catch. Never throw from this function.
```

### Architecture Decisions

```markdown
# Why We Use Prisma

Date: 2025-01-15
Decision: Use Prisma for ORM

Reasons:
- Type-safe queries
- Auto-generated migrations
- Good developer experience

Trade-offs:
- Slower than raw SQL for complex queries
- Learning curve for team

Alternatives Considered:
- TypeORM: Too complex
- Knex: No type safety
```

### Common Errors

```markdown
# ECONNREFUSED on Port 5432

This error means PostgreSQL isn't running.

Fix:
1. Check if postgres is running: `pg_isready`
2. If not: `brew services start postgresql`
3. Verify: `psql -U postgres`

Common Causes:
- Mac restart (postgres doesn't auto-start)
- Port conflict with Docker
```

### Team Conventions

```markdown
# PR Description Format

Every PR must include:

## Summary
[What this PR does]

## Changes
- [Bullet list of changes]

## Testing
- [ ] Unit tests pass
- [ ] Manual testing done
- [ ] Screenshots attached (if UI)

## Reviewers
@team-lead for architectural changes
@qa for anything user-facing
```

---

## Saving to Knowledge Base

### Method 1: From Conversation

```
You: Save this authentication pattern to the knowledge base
Agent: Saved "Authentication Pattern" to knowledge base.
       Tags: #auth #code-pattern #typescript
```

### Method 2: From Agent Manager

1. Select text in conversation
2. Right-click → "Save to Knowledge"
3. Add title and tags
4. Confirm

### Method 3: Manual Entry

1. Open Knowledge Base (Cmd + K)
2. Click "Add Entry"
3. Write content
4. Add metadata (title, tags, description)
5. Save

---

## Referencing Knowledge

### Automatic Reference

Agent automatically searches KB when relevant:

```
You: Set up authentication for this project
Agent: I found a saved authentication pattern in your knowledge base.
       Using that as the foundation...
```

### Explicit Reference

```
You: Use the PR description format from my knowledge base
Agent: Found "PR Description Format". Applying that template...
```

### Search Reference

```
You: What do I have saved about database patterns?
Agent: Found 3 relevant entries:
       1. "Prisma Setup Pattern"
       2. "Database Migration Checklist"
       3. "Why We Use Prisma"
```

---

## Organizing Knowledge

### Tags

Use consistent tags:
```
#code-pattern     - Reusable code
#architecture     - Design decisions
#debugging        - Error solutions
#convention       - Team standards
#tool-config      - Tool setup
```

### Naming

Use descriptive, searchable names:
```
# Good
"React Component Testing Pattern"
"ECONNREFUSED Port 5432 Fix"
"PR Description Template"

# Bad
"Note 1"
"Code snippet"
"Remember this"
```

### Structure

Each entry should have:
```markdown
# [Descriptive Title]

## Context
[When/why to use this]

## Content
[The actual knowledge]

## Examples
[Usage examples]

## Tags
#relevant #tags #here
```

---

## Knowledge Base vs Rules

| Aspect | Knowledge Base | Rules (GEMINI.md) |
|--------|----------------|-------------------|
| **Scope** | Referenced when relevant | Always loaded |
| **Size** | Can be large | Should be concise |
| **Purpose** | Reference material | Behavioral guidelines |
| **Example** | "How we handle auth" | "Always use TypeScript" |

**Rules**: Shape behavior
**Knowledge**: Provide context

---

## Pause Point #5

**Time to practice: 3 minutes**

Go to [exercises/05-artifacts/](../exercises/05-artifacts/) and create a knowledge base entry.

---

## Best Practices

### 1. Save As You Learn

Every time you solve a tricky problem, save it:
```
"That took 2 hours. Save this solution so next time takes 2 seconds."
```

### 2. Include Context

```markdown
# Bad
npm install --legacy-peer-deps

# Good
# Legacy Peer Deps Fix

When: You see "ERESOLVE unable to resolve dependency tree"
Why: Conflicting peer dependencies between packages
Fix: npm install --legacy-peer-deps

Note: This is a bandaid. Better to resolve the actual conflict.
```

### 3. Update Regularly

Knowledge can become stale. Review periodically:
```
You: Review my knowledge base entries from over 6 months ago
Agent: Found 12 entries. Here are ones that may be outdated...
```

---

## Checkpoint

You should now be able to:

- [ ] Save context to knowledge base
- [ ] Reference knowledge in conversations
- [ ] Organize with tags and clear naming
- [ ] Know when to use KB vs rules

---

## Next

**[Segment 8: Production Setup →](./08-production-setup.md)**

Verify your complete Antigravity configuration.
