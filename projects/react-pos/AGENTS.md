# React POS Agent Rules

This project is the React POS application. It is a code project under the
SecondBrain workspace and should use the workspace knowledge vault for context
when needed.

## Paths

- Project root: `D:\ProjectAP\SecondBrain\projects\react-pos`
- Frontend: `D:\ProjectAP\SecondBrain\projects\react-pos\front-end`
- Backend: `D:\ProjectAP\SecondBrain\projects\react-pos\back-end`
- Knowledge vault: `D:\ProjectAP\SecondBrain\knowledge`

## Stack

- Frontend: React
- Backend: Node.js
- Database: Microsoft SQL Server (MSSQL)
- ORM: Prisma 6

## Routing

- Frontend/UI work goes in `front-end/`.
- Backend/API/database work goes in `back-end/`.
- Prisma schema, migrations, and database access code belong under `back-end/`.
- Knowledge/wiki/source work goes in `D:\ProjectAP\SecondBrain\knowledge`, not
  inside this project.
- If the requested target is unclear, ask before editing.

## Knowledge Access

Before implementing features that depend on existing notes, business rules,
project decisions, source material, or LLM Wiki conventions, read:

1. `D:\ProjectAP\SecondBrain\knowledge\AGENTS.md`
2. `D:\ProjectAP\SecondBrain\knowledge\index.md`
3. Relevant files under `D:\ProjectAP\SecondBrain\knowledge\wiki/`
4. Relevant workflows under `D:\ProjectAP\SecondBrain\knowledge\operations/`

If the vault path is not accessible, stop and tell the user.

## Package Manager

Use the package manager already present in the relevant folder:

- `pnpm-lock.yaml` -> use `pnpm`
- `package-lock.json` -> use `npm`
- `yarn.lock` -> use `yarn`

If no package manager files exist, do not guess silently. Ask the user or follow
an explicit stack choice from the user.

## Frontend Rules

- Use React for frontend application code.
- Keep reusable UI components focused and small.
- Keep API calls and data-access helpers separate from presentation components.
- Do not hardcode backend URLs when an environment variable is available.

## Backend Rules

- Use Node.js for backend application code.
- Use MSSQL as the database.
- Use Prisma 6 as the ORM for database schema, migrations, and typed data access.
- Keep database credentials in environment variables, never in committed files.
- Do not commit generated databases, local dumps, or secret `.env` files.

## Boundaries

- Do not place app source code inside `D:\ProjectAP\SecondBrain\knowledge`.
- Do not duplicate knowledge vault markdown inside this project.
- Do not commit `.env`, `.env.local`, `node_modules`, build outputs, coverage
  output, local database files, or generated caches.
- Keep frontend and backend concerns separated unless the user explicitly asks
  for a shared package or monorepo tooling.

## Verification

After code changes, run the available checks for the touched side:

- Frontend: lint, test, typecheck, and build when configured.
- Backend: lint, test, typecheck, Prisma validation/generation, and start/build
  checks when configured.

If checks are not configured yet, say that clearly in the final response.
