# API Service Example — Codex Memory

## Project
REST API with Express + TypeScript + PostgreSQL. JWT auth.

## Key Commands
```bash
npm run dev          # start dev server (port 3000)
npm test             # vitest
npm run db:migrate   # prisma migrate dev
npm run build        # tsc
```

## Conventions
- All routes in `src/routes/`, business logic in `src/services/`
- Middleware in `src/middleware/`
- Zod for request validation in every route handler
- All service functions are async and throw typed errors
- Tests co-located: `src/services/user.service.test.ts`

## Database
- ORM: Prisma — schema at `prisma/schema.prisma`
- Never write raw SQL — use Prisma client
- Run `npm run db:migrate` after schema changes

## Auth
- Access token: 15 min expiry
- Refresh token: 7 day expiry, stored in httpOnly cookie
- Auth middleware: `src/middleware/auth.middleware.ts`
