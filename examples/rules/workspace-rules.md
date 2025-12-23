# Example Workspace Rules

This file goes in `[project]/.agent/rules/conventions.md`

---

# Project: E-commerce Platform

## Tech Stack

### Frontend
- Next.js 14 with App Router
- TypeScript (strict mode)
- Tailwind CSS
- React Query for data fetching

### Backend
- Node.js with Express
- TypeScript
- Prisma ORM
- PostgreSQL database

### Infrastructure
- Docker for local development
- GitHub Actions for CI/CD
- AWS for hosting

---

## Directory Structure

```
src/
├── app/                    # Next.js pages (App Router)
├── components/             # Reusable UI components
│   ├── ui/                 # Base components (Button, Input, etc.)
│   └── features/           # Feature-specific components
├── lib/                    # Utilities and helpers
├── hooks/                  # Custom React hooks
├── types/                  # TypeScript type definitions
├── api/                    # API route handlers
└── prisma/                 # Database schema and migrations
```

---

## Naming Conventions

### Files
- Components: PascalCase (`ProductCard.tsx`)
- Utilities: camelCase (`formatPrice.ts`)
- Types: PascalCase with suffix (`ProductType.ts`)
- Hooks: camelCase with "use" prefix (`useCart.ts`)

### Components
- Props interface named `[Component]Props`
- Export named, not default
- One component per file

### API
- Route files: lowercase with dashes (`user-profile.ts`)
- Handler functions: camelCase (`getUserProfile`)

---

## Database

### Prisma
- Model names: PascalCase singular (`User`, `Product`)
- Field names: camelCase (`createdAt`, `userId`)
- Use explicit relation names

### Migrations
- Always create migration for schema changes
- Never edit production database directly
- Test migrations on staging first

### Queries
- Use transactions for multi-table operations
- Include proper error handling
- Log slow queries (>100ms)

---

## API Design

### Endpoints
- REST conventions
- Versioned: `/api/v1/...`
- Resources plural: `/products`, `/users`

### Responses
```json
{
  "data": {},
  "error": null
}
```

### Error Responses
```json
{
  "data": null,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid email format"
  }
}
```

---

## Component Patterns

### Server Components (default)
- For data fetching
- For static content
- When no interactivity needed

### Client Components (use 'use client')
- For interactivity (onClick, onChange)
- For hooks (useState, useEffect)
- For browser APIs

### Data Fetching
- Use React Query for client-side
- Use server components for initial load
- Implement proper loading states

---

## Testing

### Unit Tests
- Jest + React Testing Library
- Test file: `*.test.ts(x)`
- Located next to source file

### Integration Tests
- Playwright for E2E
- Test critical user flows
- Run before deploy

### Test Coverage
- Aim for 80%+ on business logic
- Don't test styling or simple getters
- Focus on behavior, not implementation

---

## Environment Variables

### Required
```
DATABASE_URL=
NEXT_PUBLIC_API_URL=
```

### Optional
```
LOG_LEVEL=info
ENABLE_ANALYTICS=false
```

### Never Commit
- API keys
- Secrets
- Production credentials
