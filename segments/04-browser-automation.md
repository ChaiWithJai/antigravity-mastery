# Segment 4: Browser Automation

**Duration: 25 minutes**

---

## Learning Objectives

By the end of this segment, you will:
- Configure the Chrome extension for browser automation
- Request browser-based verification from agents
- Set up URL allowlists for security

---

## Why Browser Automation?

Traditional verification:
```
Agent: "I made the changes"
You: [Opens browser, manually checks]
```

With browser automation:
```
Agent: "I made the changes. Here's a screenshot proving it works."
       [Screenshot artifact attached]
```

**The agent proves its work. You review the proof.**

---

## Setup Review

If you completed SETUP.md, you already have:
- Chrome extension installed
- Basic permissions granted

### Verify Setup

In Agent Manager:
```
You: Go to google.com and take a screenshot
Agent: [Opens Chrome, navigates, captures screenshot]
```

If this works, you're ready.

---

## Browser Capabilities

| Capability | Example |
|------------|---------|
| Navigate | "Go to localhost:3000" |
| Screenshot | "Take a screenshot" |
| Record | "Record a walkthrough" |
| Interact | "Click the login button" |
| Fill forms | "Enter test@example.com in email field" |
| Wait | "Wait for the loading spinner to disappear" |

---

## Verification Patterns

### Pattern 1: Screenshot Proof

```
You: Build a login form, then show me a screenshot of it
Agent: [Builds form, starts dev server, takes screenshot]
       📸 Screenshot: login-form.png
```

### Pattern 2: Recorded Walkthrough

```
You: Implement the checkout flow, then record yourself going through it
Agent: [Implements checkout]
       🎬 Recording: checkout-walkthrough.mp4

       The walkthrough shows:
       1. Adding item to cart
       2. Proceeding to checkout
       3. Entering payment info
       4. Completing purchase
```

### Pattern 3: Automated Testing

```
You: Add form validation, then test all error states
Agent: [Implements validation]

       Testing error states:
       📸 Empty email: shows "Email required"
       📸 Invalid email: shows "Invalid email format"
       📸 Short password: shows "Minimum 8 characters"

       All validations working correctly.
```

---

## URL Allowlist

For security, agents can only visit allowed URLs.

### Location
```
~/.gemini/antigravity/browserAllowlist.txt
```

### Format
```
localhost
localhost:3000
localhost:*
127.0.0.1
*.mycompany.com
staging.myapp.com
```

### Default Allowed
- localhost (all ports)
- 127.0.0.1
- URLs you've previously approved

### Adding URLs

**Option 1: Manual**
Edit `~/.gemini/antigravity/browserAllowlist.txt`

**Option 2: Runtime Approval**
When agent tries to visit blocked URL:
```
Agent: I need to visit staging.example.com. Allow?
[Allow Once] [Allow Always] [Deny]
```

"Allow Always" adds to allowlist.

---

## Browser Commands

### Navigation
```
Go to [URL]
Open [URL] in browser
Navigate to [URL]
```

### Capture
```
Take a screenshot
Screenshot the current page
Capture the login form
```

### Recording
```
Record a walkthrough of [action]
Start recording
Stop recording
```

### Interaction
```
Click the [element]
Fill in [field] with [value]
Select [option] from [dropdown]
Scroll down
Wait for [element/text]
```

---

## Practical Example

### Building and Verifying a Feature

```
You: Build a user profile page with:
     - Avatar upload
     - Name and bio fields
     - Save button

     Then test it by:
     1. Going to /profile
     2. Uploading a test image
     3. Filling in the fields
     4. Clicking save
     5. Refreshing to verify it persisted

     Take screenshots at each step.
```

Agent produces:
- Code for profile page
- Screenshot: Empty profile form
- Screenshot: After filling fields
- Screenshot: After upload
- Screenshot: Success message
- Screenshot: After refresh (data persisted)

**You can verify the entire flow from artifacts.**

---

## Troubleshooting Browser

### "Browser not responding"

1. Check Chrome extension is enabled
2. Restart Chrome
3. Restart Antigravity

### "URL not allowed"

1. Check allowlist file
2. Add URL pattern
3. Or approve at runtime

### "Element not found"

Agent may be too fast. Ask for:
```
Wait for the page to fully load before clicking
```

### "Screenshot is blank"

Page may not have rendered:
```
Wait 2 seconds, then take a screenshot
```

---

## Security Considerations

### What to Allowlist
- Development servers (localhost)
- Staging environments
- Internal tools

### What NOT to Allowlist
- Production with real user data
- Banking/financial sites
- Sites with sensitive credentials

### Principle
**Agents should verify in safe environments, not production.**

---

## Pause Point #4

**Time to practice: 5 minutes**

Go to [exercises/04-browser-automation/](../exercises/04-browser-automation/) and configure browser automation for a task.

---

## Checkpoint

You should now be able to:

- [ ] Verify Chrome extension is working
- [ ] Request screenshots and recordings
- [ ] Configure URL allowlist
- [ ] Build verification into your workflows

---

## Next

**[Segment 5: Artifacts & Trust →](./05-artifacts-trust.md)**

Learn to read and request different artifact types.
