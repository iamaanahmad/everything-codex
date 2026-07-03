# Web App Example — Codex Memory

## Project
Full-stack web app: Next.js 15 (App Router) + TypeScript + Tailwind + PostgreSQL.

## Key Commands
```bash
npm run dev      # Next.js dev server (port 3000)
npm test         # vitest + playwright
npm run build    # production build
npm run db:push  # push Prisma schema changes
```

## Conventions
- App Router: pages in `app/`, components in `components/`
- Server Components by default — add `"use client"` only when needed
- API routes in `app/api/`
- Tailwind for all styling — no CSS modules or styled-components
- Zod for form validation (client + server)

## Deployment
- Vercel (use `vercel-deploy-skill`)
- Environment variables set in Vercel dashboard
- Preview deployments on every PR
