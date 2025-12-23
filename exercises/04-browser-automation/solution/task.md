# Browser Automation Task

## Complete Prompt

```
Create a simple contact form webpage and verify it works.

## Step 1: Create the HTML file

Create `contact.html` with:
- Name input (required)
- Email input (required, type="email")
- Message textarea (required)
- Submit button
- Basic styling (centered, clean look)
- Form validation feedback

## Step 2: Serve the page

Start a simple HTTP server on port 8000:
```bash
python3 -m http.server 8000
```

## Step 3: Verify the form

1. Navigate to http://localhost:8000/contact.html
2. Take a screenshot of the empty form
3. Fill in:
   - Name: "Test User"
   - Email: "test@example.com"
   - Message: "This is a test message"
4. Take a screenshot of the filled form
5. Try to submit with empty fields first - screenshot the validation errors
6. Fill in all fields and submit
7. Take a screenshot of the success state

## Expected Artifacts

Provide these screenshots:
1. Empty form
2. Filled form
3. Validation errors
4. Success state
```

---

## Expected Output

The agent should produce:

### Code: contact.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Contact Form</title>
  <style>
    /* Clean styling */
  </style>
</head>
<body>
  <form id="contactForm">
    <input name="name" required placeholder="Name">
    <input name="email" type="email" required placeholder="Email">
    <textarea name="message" required placeholder="Message"></textarea>
    <button type="submit">Send</button>
  </form>
</body>
</html>
```

### Artifacts
1. Screenshot: Empty form
2. Screenshot: Form with test data filled
3. Screenshot: Validation error state
4. Screenshot: Success message

---

## Why This Exercise Matters

- Proves browser automation works
- Shows agent can interact with forms
- Demonstrates screenshot artifact creation
- Verifies end-to-end workflow
