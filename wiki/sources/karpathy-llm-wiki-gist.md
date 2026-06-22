---
type: source
status: active
created: 2026-06-23
updated: 2026-06-23
tags:
  - wiki/source
  - llm-wiki
source_type: gist
source_url: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
author: Andrej Karpathy
---

# Karpathy LLM Wiki Gist

## Source

- URL: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- Author: [[wiki/people/andrej-karpathy]]
- Date created on GitHub gist page: 2026-04-04

## Summary

The gist proposes a personal knowledge base pattern where an LLM maintains a
persistent wiki from curated raw sources. Instead of treating retrieval as a
one-time lookup over chunks, the system compiles knowledge into linked markdown
pages that improve over time.

## Key Ideas

- Separate immutable raw sources from the maintained wiki.
- Store schema and workflows in an agent-readable file such as `AGENTS.md`.
- Use `index.md` for content navigation and `log.md` for chronology.
- Ingest sources by updating many related pages, not just by writing one
  summary.
- File reusable query answers back into the wiki.
- Run periodic lint passes to catch broken links, stale claims, or missing pages.

## Pages Created Or Updated

- [[wiki/topics/llm-wiki]]
- [[wiki/topics/second-brain]]
- [[wiki/maps/llm-wiki-architecture]]
- [[wiki/concepts/compiled-knowledge]]
- [[wiki/concepts/source-of-truth]]
- [[wiki/concepts/wiki-as-codebase]]
- [[wiki/syntheses/second-brain-llm-wiki-operating-model]]

## Open Questions

- Which personal domains should be modeled first as areas?
- Should source ingestion stay fully supervised or allow batch processing?
- When the vault grows, should search remain index-based or add a local search
  tool?
