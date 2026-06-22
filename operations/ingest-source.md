---
type: operation
status: active
created: 2026-06-23
updated: 2026-06-23
tags:
  - operation/ingest
---

# Ingest Source

Use this workflow when a new source is added to `raw/inbox/` or supplied by the
user.

## Steps

1. Identify the source, author, date, format, and location.
2. Move or copy accepted evidence into `raw/sources/` when appropriate.
3. Create a source brief from [[templates/source-brief]] in `wiki/sources/`.
4. Extract important entities, people, concepts, topics, projects, and areas.
5. Update existing wiki pages before creating duplicates.
6. Create new pages from templates when a concept is important enough to stand
   alone.
7. Record contradictions or uncertainty explicitly.
8. Update [[index]].
9. Append an entry to [[log]].

## Quality Bar

- The source brief links to raw evidence or the original URL.
- All important new pages have frontmatter.
- The index lists new durable pages.
- The log records what changed and why.
