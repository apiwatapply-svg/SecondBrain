---
type: project
status: seed
created: 2026-06-27
updated: 2026-06-27
tags:
  - wiki/project
  - react
source_count: 1
---

# React POS

## Outcome

Build a point-of-sale application using the registered project at
`projects/react-pos`, with React on the frontend, Node.js on the backend, MSSQL
as the database, and Prisma 6 as the ORM.

## Context

- Workspace project path: `projects/react-pos`
- Frontend path: `projects/react-pos/front-end`
- Backend path: `projects/react-pos/back-end`
- Project-specific agent rules: `projects/react-pos/AGENTS.md`
- Related knowledge: [[wiki/topics/react]]

## Current Plan

- Keep app code under `projects/react-pos/`, not inside the Obsidian vault.
- Use the knowledge vault for durable decisions, business rules, source briefs,
  and implementation context.
- Decide frontend package manager and app scaffold before writing production
  frontend code.

## Decisions

- Frontend stack: React.
- Backend stack: Node.js.
- Database: Microsoft SQL Server.
- ORM: Prisma 6.
- React documentation source collection is available as
  [[wiki/sources/react-19-official-docs]].

## Related

- [[wiki/topics/react]]
- [[wiki/entities/react]]
- [[wiki/sources/react-19-official-docs]]
