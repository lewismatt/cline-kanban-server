# Cline Kanban Server

A lightweight REST API server for managing kanban board data — boards, columns, cards, and user assignments. Designed as the backend layer for kanban front-end clients.

## Tech Stack

| Layer | Choice | Rationale |
|---|---|---|
| Runtime | Node.js | Ubiquitous JavaScript runtime; large ecosystem |
| Language | TypeScript | Type safety, IDE tooling, maintainability for shared models |
| Framework | Express.js | Mature, minimal API framework with broad middleware support |
| Auth | JWT | Stateless token auth suitable for REST APIs |
| Database | PostgreSQL + node-postgres | ACID guarantees for ordered kanban state; pg is a well-known driver |
| ORM / Query | (TBD) | Candidates: Prisma or Drizzle ORM for type-safe DB access |

## Prerequisites

- Node.js 20 LTS or later
- PostgreSQL 15 or later (local or hosted)
- npm 10+

## Installation

1. Clone the repository.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Copy the environment example and fill in your values:
   ```bash
   cp .env.example .env
   ```
4. Create the database and run migrations (once migration tooling is in place).

## Environment Variables

| Variable | Description | Example |
|---|---|---|
| `PORT` | Port the API server listens on | `3000` |
| `NODE_ENV` | Runtime environment | `development`, `production`, `test` |
| `DATABASE_URL` | PostgreSQL connection string | `postgres://user:pass@localhost:5432/kanban` |
| `JWT_SECRET` | Secret used to sign and verify JWT tokens | `replace-me-with-a-secure-random-string` |
| `CORS_ORIGIN` | Allowed origin(s) for CORS — comma-separated | `http://localhost:5173` |
| `RATE_LIMIT_MAX` | Max requests per IP per rate-limit window | `100` |

## Running

```bash
npm run start
```

The API will be available at `http://localhost:3000`.

## Project Structure

```
.
├── src/
│   ├── index.ts          # Entry point — server bootstrap
│   ├── routes/           # Route definitions / route handlers
│   ├── controllers/      # Request handlers / orchestrating logic
│   ├── services/         # Domain logic and external call wrappers
│   ├── models/           # TypeScript types, schemas, ORM entities
│   └── middleware/       # Auth, validation, error-handling middleware
├── .env.example          # Documented environment variable template
├── package.json          # Project metadata and scripts
└── README.md             # This file
```

## Contributing

1. Fork and branch from `main`.
2. Install dependencies with `npm install`.
3. Make your changes and add tests if applicable.
4. Run quality gates before opening a pull request:
   ```
   npm run lint   &&  npm run build
   ```
5. Open a Pull Request against `main`. Keep commits small and scoped to one concern.

## Architecture

_To be documented in a future update._

This section will describe: layered architecture diagram, request → middleware → controller → service → model data flow, database ERD (board / column / card / user / membership), authentication and authorization strategy, rate-limiting and error-handling strategy, and planned API versioning approach.
