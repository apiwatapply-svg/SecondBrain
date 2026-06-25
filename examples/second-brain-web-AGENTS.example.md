# SecondBrain Web Agent Rules Example

Use this as a starting point when creating a real web project under
`projects/<project-name>/AGENTS.md`.

Replace `second-brain-web` with the actual project folder name.

## Project

This project is a web frontend/backend for the SecondBrain knowledge vault.

## Paths

- App code: `D:\ProjectAP\SecondBrain\projects\second-brain-web`
- Knowledge vault: `D:\ProjectAP\SecondBrain\knowledge`
- Vault env var: `SECOND_BRAIN_VAULT_PATH`

## Knowledge Access

Before implementing features that depend on notes, wiki structure, ingest,
search, templates, source processing, or Obsidian behavior, read:

1. `D:\ProjectAP\SecondBrain\knowledge\AGENTS.md`
2. `D:\ProjectAP\SecondBrain\knowledge\index.md`
3. Relevant files under `D:\ProjectAP\SecondBrain\knowledge\operations/`
4. Relevant files under `D:\ProjectAP\SecondBrain\knowledge\wiki/`

If the vault path is not accessible, stop and tell the user.

## App Rules

- Do not duplicate knowledge files inside this app project.
- Read and write vault markdown through `SECOND_BRAIN_VAULT_PATH`.
- Keep secrets in `.env.local`.
- Commit `.env.example`, never commit `.env.local`.
- Do not commit generated build output.
