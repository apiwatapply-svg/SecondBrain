# SecondBrain Workspace

This repository is the workspace root for the SecondBrain system. It contains the
knowledge vault and, later, code projects that use that vault.

## Paths

- Workspace root: `D:\ProjectAP\SecondBrain`
- Knowledge vault: `D:\ProjectAP\SecondBrain\knowledge`
- Projects root: `D:\ProjectAP\SecondBrain\projects`

## Routing Rules

Before editing files, identify the task type.

- If the task is about notes, sources, wiki pages, ingest, query, lint,
  templates, or Obsidian knowledge management, work in `knowledge/`.
- If the task is about application code, frontend, backend, APIs, database,
  deployment, tests, or UI, work in `projects/<project-name>/` after the target
  project folder exists.
- If the task depends on existing knowledge, read:
  1. `knowledge/AGENTS.md`
  2. `knowledge/index.md`
  3. relevant files under `knowledge/wiki/`
  4. relevant workflows under `knowledge/operations/`

If the target project is unclear or the project folder does not exist, ask before
editing code.

## Examples

- Use examples/second-brain-web-AGENTS.example.md as a starter when creating a future web app project.

## Project Registration

No code projects are registered yet.

When a project is created, add its folder under `projects/` and document:

- Project name
- Code path
- Knowledge path
- Purpose
- Any project-specific agent rules

## Boundaries

- Do not put app source code inside `knowledge/`.
- Do not put Obsidian vault knowledge files inside app project folders.
- Do not commit `node_modules`, `.next`, build outputs, local database files,
  or `.env.local`.
- Do not modify `knowledge/.obsidian/` unless the user explicitly asks.

## Git

- Default branch: `main`
- Remote: `https://github.com/apiwatapply-svg/SecondBrain.git`

