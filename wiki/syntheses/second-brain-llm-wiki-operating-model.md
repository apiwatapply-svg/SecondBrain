---
type: synthesis
status: seed
created: 2026-06-23
updated: 2026-06-23
tags:
  - wiki/synthesis
  - second-brain
  - llm-wiki
source_count: 1
---

# Second Brain LLM Wiki Operating Model

## Thesis

This vault should begin as a general second brain with an LLM Wiki core. That
keeps the architecture flexible enough for personal, research, career, business,
and reading notes while still enforcing strong source and maintenance rules.

## Operating Principles

- Capture broadly, then ingest deliberately.
- Keep raw evidence separate from interpretation.
- Let wiki pages become the durable memory, not chat history.
- Update existing pages when new sources arrive.
- Use `index.md` and `log.md` as the system's memory spine.

## First Useful Milestones

1. Add 3-5 real sources to `raw/inbox/`.
2. Ingest them one by one using [[operations/ingest-source]].
3. Create the first area pages in `wiki/areas/`.
4. Run [[operations/lint-wiki]] after the initial batch.

## Source

- [[wiki/sources/karpathy-llm-wiki-gist]]
