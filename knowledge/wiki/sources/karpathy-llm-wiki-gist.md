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
raw_file: raw/sources/2026-06-23-karpathy-llm-wiki.md
author: Andrej Karpathy
---

# Karpathy LLM Wiki Gist

## Source

- Raw file: [[raw/sources/2026-06-23-karpathy-llm-wiki]]
- URL: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- Author: [[wiki/people/andrej-karpathy]]
- Captured: 2026-06-23

## Summary

The gist proposes a personal knowledge base pattern where an LLM maintains a
persistent wiki from curated raw sources. Instead of treating retrieval as a
one-time lookup over chunks, the system compiles knowledge into linked markdown
pages that improve over time.

## Key Claims

- Raw sources should stay separate from the maintained wiki.
  - Evidence: the source defines raw sources as immutable source-of-truth files.
  - Related pages: [[wiki/concepts/source-of-truth]], [[raw/README]].
- The wiki should be a persistent, compounding artifact rather than a temporary
  retrieval result.
  - Evidence: the source contrasts incremental wiki maintenance with RAG-style
    rediscovery on every query.
  - Related pages: [[wiki/concepts/compiled-knowledge]], [[wiki/topics/llm-wiki]].
- The LLM should own wiki maintenance while the human curates sources, asks
  questions, and reviews results.
  - Evidence: the source frames Obsidian as the IDE, the LLM as the programmer,
    and the wiki as the codebase.
  - Related pages: [[wiki/concepts/wiki-as-codebase]], [[AGENTS]].
- `index.md` and `log.md` make a markdown wiki navigable without needing a full
  retrieval system at small to moderate scale.
  - Evidence: the source describes `index.md` as content-oriented and `log.md`
    as chronological.
  - Related pages: [[index]], [[log]].
- Good query answers should be filed back into the wiki when reusable.
  - Evidence: the source describes query answers as pages, comparisons,
    analyses, or other durable artifacts that should not disappear into chat.
  - Related pages: [[operations/query-wiki]], [[operations/promote-chat-answer]].
- Periodic lint passes should detect contradictions, stale claims, orphan pages,
  missing concepts, and missing cross-references.
  - Evidence: the source names lint as a core operation.
  - Related pages: [[operations/lint-wiki]].

## Pages Created Or Updated

- [[wiki/topics/llm-wiki]]
- [[wiki/topics/second-brain]]
- [[wiki/maps/llm-wiki-architecture]]
- [[wiki/concepts/compiled-knowledge]]
- [[wiki/concepts/source-of-truth]]
- [[wiki/concepts/wiki-as-codebase]]
- [[wiki/syntheses/second-brain-llm-wiki-operating-model]]
- [[operations/ingest-source]]
- [[operations/query-wiki]]
- [[operations/lint-wiki]]
- [[operations/promote-chat-answer]]
- [[index]]
- [[log]]
- [[wiki/people/262588213843476]]

## Conflicts

- None known.

## Open Questions

- Which personal domains should be modeled first as areas?
- Should source ingestion stay fully supervised or allow batch processing?
- When the vault grows, should search remain index-based or add a local search
  tool such as qmd?

