---
type: map
status: seed
created: 2026-06-23
updated: 2026-06-23
tags:
  - wiki/map
  - llm-wiki
source_count: 1
---

# LLM Wiki Architecture

This vault follows a three-layer architecture.

## Layers

1. `raw/` stores curated source material.
2. `wiki/` stores LLM-maintained markdown pages.
3. `AGENTS.md` stores the schema and operating rules.

## Control Files

- [[index]] is content-oriented.
- [[log]] is chronological.
- [[AGENTS]] is procedural.

## Maintenance Loop

1. Ingest sources.
2. Update wiki pages.
3. File useful query answers.
4. Run periodic lint passes.
5. Evolve the schema when repeated friction appears.

## Source

- [[wiki/sources/karpathy-llm-wiki-gist]]
