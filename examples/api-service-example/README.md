# API Service Example

A production-ready REST API built with Node.js, Express, TypeScript, and PostgreSQL — demonstrating everything-codex patterns.

## Stack
- **Runtime**: Node.js 20 + TypeScript
- **Framework**: Express
- **Database**: PostgreSQL + Prisma ORM
- **Auth**: JWT (access + refresh tokens)
- **Testing**: Vitest + Supertest
- **Deployment**: Docker + docker-compose

## Quick Start

```bash
npm install
cp .env.example .env
npm run db:migrate
npm run dev
```

API available at `http://localhost:3000`

## Project Structure

```
src/
├── routes/          # Express route definitions
│   ├── auth.ts
│   └── users.ts
├── services/        # Business logic
│   ├── auth.service.ts
│   └── user.service.ts
├── middleware/      # Express middleware
│   ├── auth.middleware.ts
│   └── validate.middleware.ts
├── models/          # Prisma schema + generated client
├── utils/           # Shared helpers
└── index.ts         # App entry point
```

## Endpoints

| Method | Path | Auth | Description |
|--------|------|------|-------------|
| POST | `/auth/register` | — | Register new user |
| POST | `/auth/login` | — | Login, returns JWT |
| POST | `/auth/refresh` | — | Refresh access token |
| GET | `/users/me` | ✅ | Get current user |
| PATCH | `/users/me` | ✅ | Update profile |
| GET | `/users` | ✅ Admin | List all users |

## Codex Skills Used

- `tdd-workflow-skill` — all endpoints built test-first
- `code-review-skill` — security review before each PR
- `api-docs-skill` — OpenAPI spec at `docs/openapi.yaml`
- `docker-deploy-skill` — containerized with multi-stage Dockerfile

## Environment Variables

```bash
DATABASE_URL=postgresql://user:password@localhost:5432/mydb
JWT_SECRET=<strong-random-secret>
JWT_REFRESH_SECRET=<different-strong-random-secret>
PORT=3000
NODE_ENV=development
```

## Scripts

```bash
npm run dev          # dev server with hot reload
npm test             # run test suite
npm run test:watch   # watch mode
npm run db:migrate   # run Prisma migrations
npm run db:studio    # open Prisma Studio
npm run build        # compile TypeScript
npm run docker:up    # start with docker-compose
```
