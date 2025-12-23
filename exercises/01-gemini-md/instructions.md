# Exercise 1: Create Your GEMINI.md

**Duration: 3 minutes**

---

## Objective

Create your global GEMINI.md file with at least 3 rules.

---

## Steps

### Step 1: Create the file

```bash
mkdir -p ~/.gemini
touch ~/.gemini/GEMINI.md
```

Or in Antigravity:
- Cmd + Shift + P
- "Open GEMINI.md"

### Step 2: Add your rules

Include at minimum:

1. **One code style rule**
   - Language preference
   - Framework preference
   - Formatting standard

2. **One safety rule**
   - What should never auto-execute
   - What always needs confirmation

3. **One communication rule**
   - How agent should explain actions
   - How agent should report completion

### Step 3: Save and test

1. Save the file
2. Start a new conversation in Agent Manager
3. Ask the agent to describe something related to your rules
4. Verify it follows your preferences

---

## Success Criteria

- [ ] `~/.gemini/GEMINI.md` exists
- [ ] Contains at least 3 meaningful rules
- [ ] Agent behavior changes based on rules

---

## Example

See [solution/GEMINI.md](./solution/GEMINI.md) for a complete example.

---

## Common Mistakes

**Too vague:**
```markdown
# Bad
Be helpful and write good code
```

**Too restrictive:**
```markdown
# Bad
Never use any npm packages
Always ask before every single action
```

**Good balance:**
```markdown
# Good
- Use TypeScript for JavaScript projects
- Never run `rm -rf` without explicit confirmation
- Explain what you're about to do before complex operations
```
