# Exercise 4: Browser Automation

**Duration: 5 minutes**

---

## Objective

Configure browser automation and have the agent verify its own work.

---

## Steps

### Step 1: Verify Chrome extension

In Agent Manager, type:
```
Go to google.com and take a screenshot
```

If this fails:
1. Check Chrome extension is installed
2. Go to Settings → Browser → Re-authenticate

### Step 2: Configure allowlist (if needed)

Add your development URLs:
```bash
echo "localhost" >> ~/.gemini/antigravity/browserAllowlist.txt
echo "localhost:3000" >> ~/.gemini/antigravity/browserAllowlist.txt
echo "localhost:*" >> ~/.gemini/antigravity/browserAllowlist.txt
```

### Step 3: Create a simple webpage

Ask the agent:
```
Create a simple contact form with:
- Name field
- Email field
- Message textarea
- Submit button

Save it as contact.html and serve it on localhost:8000
```

### Step 4: Request verification

```
Now go to localhost:8000 and:
1. Fill in the form with test data
2. Take a screenshot showing the filled form
3. Click submit
4. Take a screenshot of the result
```

### Step 5: Review artifacts

Check that you received:
- Screenshot of empty form
- Screenshot of filled form
- Screenshot after submission

---

## Success Criteria

- [ ] Chrome extension working
- [ ] Agent can navigate to localhost
- [ ] Agent produces screenshot artifacts
- [ ] Agent can interact with page elements

---

## Troubleshooting

**"URL not allowed"**
- Add URL to `~/.gemini/antigravity/browserAllowlist.txt`

**"Element not found"**
- Agent may be too fast; ask it to wait for page load

**"Screenshot is blank"**
- Page may not have rendered; add delay

---

## Example

See [solution/task.md](./solution/task.md) for a complete example.
