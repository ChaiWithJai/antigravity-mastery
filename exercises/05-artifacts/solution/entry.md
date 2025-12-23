# Example Knowledge Base Entry

## Title
JWT Authentication Pattern (Node.js)

## Tags
#auth #jwt #node #express #security

## Content

```markdown
# JWT Authentication Pattern

## When to Use
- API authentication between frontend and backend
- Stateless authentication (no session storage)
- When you need token-based auth with expiration

## Implementation

### 1. Install Dependencies
```bash
npm install jsonwebtoken bcryptjs
```

### 2. Token Generation
```typescript
import jwt from 'jsonwebtoken';

const generateToken = (userId: string): string => {
  return jwt.sign(
    { userId },
    process.env.JWT_SECRET!,
    { expiresIn: '24h' }
  );
};
```

### 3. Token Verification Middleware
```typescript
import { Request, Response, NextFunction } from 'express';
import jwt from 'jsonwebtoken';

interface AuthRequest extends Request {
  userId?: string;
}

export const authMiddleware = (
  req: AuthRequest,
  res: Response,
  next: NextFunction
) => {
  const token = req.headers.authorization?.split(' ')[1];

  if (!token) {
    return res.status(401).json({ error: 'No token provided' });
  }

  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET!) as { userId: string };
    req.userId = decoded.userId;
    next();
  } catch {
    return res.status(401).json({ error: 'Invalid token' });
  }
};
```

### 4. Usage in Routes
```typescript
app.get('/api/protected', authMiddleware, (req: AuthRequest, res) => {
  res.json({ userId: req.userId });
});
```

## Security Considerations
- Store JWT_SECRET in environment variables
- Use HTTPS in production
- Consider refresh tokens for long-lived sessions
- Token expiration: 24h for web, shorter for mobile
- Never store sensitive data in token payload

## Common Errors

### "jwt malformed"
Token format is wrong. Ensure format is: `Bearer <token>`

### "jwt expired"
Token has expired. Implement refresh token flow or re-authenticate.

### "invalid signature"
JWT_SECRET mismatch between token generation and verification.

## Alternatives
- For sessions: express-session with Redis
- For OAuth: passport.js
- For full auth solution: Auth0, Clerk, or Supabase Auth
```

---

## Why This Entry is Good

1. **Clear title**: Searchable, specific
2. **Useful tags**: Multiple relevant categories
3. **Complete content**:
   - When to use (context)
   - How to implement (code)
   - Security notes (important considerations)
   - Error solutions (troubleshooting)
   - Alternatives (other options)
4. **Copy-pasteable code**: Ready to use
5. **Explains tradeoffs**: Helps decision-making
