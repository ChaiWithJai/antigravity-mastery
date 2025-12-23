# Multi-Agent Scenario: Blog Platform

## Setup

Two agents working on different parts of a blog platform.

---

## Agent 1: Backend

**Workspace**: `blog-backend/`

**Prompt**:
```
Build a blog post API with the following endpoints:

- GET /api/posts - List all posts (paginated)
- GET /api/posts/:id - Get single post
- POST /api/posts - Create post (requires auth)
- PUT /api/posts/:id - Update post (requires auth)
- DELETE /api/posts/:id - Delete post (requires auth)

Use Express.js with TypeScript.
Use Prisma for database.
Include proper error handling and validation.

When done, show me example curl commands for each endpoint.
```

---

## Agent 2: Frontend

**Workspace**: `blog-frontend/`

**Prompt**:
```
Build a blog post listing page with:

- List of posts with title, excerpt, and date
- Click to view full post
- Pagination controls
- Loading states
- Error handling

Use Next.js 14 with App Router.
Use Tailwind CSS for styling.
Assume the API is at http://localhost:3001/api

When done, take a screenshot of the listing page.
```

---

## Coordination Points

### After Agent 1 completes:

Share with Agent 2:
```
The backend is ready. Here are the endpoints:
- GET /api/posts - Returns { posts: [], total: number, page: number }
- Each post has: id, title, content, excerpt, createdAt, author

Update the frontend to match this structure.
```

### After Agent 2 completes:

Verify integration:
```
Start both servers and verify the frontend fetches from the backend correctly.
```

---

## Expected Artifacts

### From Agent 1:
- Task List (API endpoints)
- Implementation Plan (Express setup)
- Code Diffs (route files, models)
- Example curl commands

### From Agent 2:
- Task List (UI components)
- Implementation Plan (Next.js pages)
- Code Diffs (components, pages)
- Screenshots of UI

---

## Why This Works

- Tasks are independent (can work in parallel)
- Clear boundaries (backend vs frontend)
- Minimal coordination needed
- Each agent has defined deliverables
