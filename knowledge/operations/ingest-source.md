---
type: operation
status: active
created: 2026-06-23
updated: 2026-06-27
tags:
  - operation/ingest
---

# Ingest Source

Use this runbook whenever the user says `ingest`, `injest`, asks to process raw
files, adds a source to `raw/inbox/`, or supplies a source directly in chat.

This operation follows the LLM Wiki pattern from Karpathy's gist: raw sources are
kept as the immutable evidence layer, and the LLM integrates each source into the
maintained wiki by updating multiple related pages, `index.md`, and `log.md`.

## Required Reading Order

Before editing any ingest output, read these files in order:

1. [[AGENTS]] - vault schema, evidence rules, naming, and required workflows.
2. [[index]] - current content map and existing pages to update before creating duplicates.
3. [[log]] - recent ingest/query/lint history so the new work does not repeat or conflict.
4. This file, [[operations/ingest-source]] - the ingest runbook.
5. The relevant template:
   - [[templates/source-brief]] for ordinary sources.
   - [[templates/youtube-video-source]] for YouTube videos.
6. Relevant existing wiki pages found from `index.md`, search, and backlinks.
7. The raw source itself.

If any required file is inaccessible, stop and tell the user which path is blocked.

## Inputs

Accepted input locations:

- `raw/inbox/` for new captures waiting to be processed.
- A specific file or folder supplied by the user.
- A URL or pasted source supplied in chat.
- A root-level accidental capture folder, only after confirming it belongs in the
  knowledge vault.

Never assume root-level `raw/` belongs to the vault without checking. The vault's
raw source area is `knowledge/raw/` when working from the workspace root.

## Phase 1: Intake And Classification

1. Identify every candidate source.
2. Classify each candidate:
   - article
   - documentation page
   - documentation collection
   - YouTube video
   - paper
   - book chapter
   - podcast/transcript
   - image/PDF/asset
   - conversation-derived note
   - other
3. Record source metadata when available:
   - title
   - author or organization
   - URL
   - published date
   - captured date
   - source type
   - local file path
4. Decide whether to ingest one source or a batch.
5. If multiple unrelated sources are present, ask the user before batch ingest.

## Phase 2: Raw Source Acceptance

1. Preserve raw evidence. Do not rewrite accepted raw source content during normal ingest.
2. Move or copy accepted files into `raw/sources/`.
3. Use stable filenames:
   - Single source: `YYYY-MM-DD-author-or-site-short-title.md`
   - Collection note: `YYYY-MM-DD-collection-name.md`
   - Collection folder: `YYYY-MM-DD-collection-name/`
4. Keep assets under `raw/assets/` when downloaded locally.
5. If a source is already in `raw/sources/`, do not duplicate it. Update the
   source brief instead.

## Phase 3: Metadata Normalization

For every accepted source, make sure the source brief can capture:

```yaml
---
type: source
status: active
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags:
  - wiki/source
source_type:
source_url:
raw_file:
author:
---
```

Rules:

- `raw_file` should point to the accepted raw file or collection note.
- Use `source_url` for canonical web URLs.
- Use `author` for a person or organization when known.
- If metadata is missing, preserve the gap in `Open Questions` instead of inventing it.

## Phase 4: YouTube Web Clipper Videos

When the source is a YouTube video from Obsidian Web Clipper, `youtube.com`, or
`youtu.be`, use [[templates/youtube-video-source]].

Required steps:

1. Open or inspect the canonical YouTube URL during processing.
2. Pull the channel name from YouTube page metadata, visible page data, or a
   reliable YouTube metadata endpoint.
3. Add these frontmatter fields to the accepted source note when possible and to
   the source brief always:
   - `source_type: youtube-video`
   - `channel_name: <verified channel name>`
   - `channel_url: <channel URL when available>`
   - `video_id: <YouTube video id when available>`
4. Do not infer `channel_name` only from the clip title, filename, or transcript.
5. If the channel cannot be verified, use `channel_name: needs-review`, keep the
   source URL, add an `Open Questions` note, and mention the gap in [[log]].

## Phase 5: Source Brief Creation

1. Create or update one page in `wiki/sources/` for each source or coherent source collection.
2. Use [[templates/source-brief]] unless a source-specific template applies.
3. The source brief must include:
   - canonical source metadata
   - raw file link
   - short summary
   - key claims with evidence
   - pages created or updated
   - conflicts
   - open questions
4. Prefer collection-level source briefs for many closely related docs, such as
   a complete official documentation set.
5. Do not create one source brief per page for large documentation batches unless
   the user explicitly asks.

## Phase 6: Wiki Graph Integration

Before creating new wiki pages, search existing pages under `wiki/` and use
[[index]] to find likely matches.

For each important extracted item:

1. Update existing pages first.
2. Create a new page only when the item is important enough to be reused.
3. Choose the correct page type:
   - `wiki/topics/` for broad subjects
   - `wiki/concepts/` for reusable ideas
   - `wiki/entities/` for products, organizations, tools, places, datasets
   - `wiki/people/` for people
   - `wiki/projects/` for time-bounded efforts
   - `wiki/areas/` for long-running responsibilities
   - `wiki/syntheses/` for cross-source analysis
   - `wiki/questions/` for reusable answers from chat
4. Use the relevant template from `templates/`.
5. Add backlinks between source briefs and every page they materially update.
6. Preserve contradictions in `Conflicts` or `Open Questions` sections.
7. Update `updated:` frontmatter on pages that materially change.

## Phase 7: Index Update

Update [[index]] after wiki pages change.

Required index updates:

- Add new durable pages to the correct category.
- Update one-line summaries if page meaning changed.
- Keep source briefs listed under `Sources`.
- Keep project pages listed under `Projects`.
- Do not list temporary scratch notes.

## Phase 8: Log Update

Append an entry to [[log]] for every ingest.

Use this heading format exactly:

```markdown
## [YYYY-MM-DD] ingest | Source Or Batch Title
```

The log entry should include:

- accepted raw file or folder
- source brief path
- important wiki pages created or updated
- conflicts or metadata gaps
- whether YouTube `channel_name` rules applied

## Phase 9: Verification

Before final response:

1. Check git status and identify unrelated dirty files.
2. Check that new wikilinks resolve when practical.
3. Confirm raw files are under `raw/sources/` or explain why not.
4. Confirm source briefs link to raw evidence.
5. Confirm `index.md` and `log.md` changed when durable wiki pages changed.
6. Do not stage unrelated files from other tasks.

If verification finds broken links, missing source links, or unclear metadata,
fix them before finishing or report the blocker.

## Final Response Format

When ingest is complete, report:

- source(s) accepted
- raw path(s)
- source brief path(s)
- important wiki pages created or updated
- any metadata gaps or conflicts
- verification performed
- commit hash if a commit was made

## Quality Bar

An ingest is complete only when:

- Raw evidence is preserved.
- A source brief exists and links to the raw evidence.
- Existing wiki pages were updated before duplicates were created.
- Important concepts/entities/topics/projects were connected with wikilinks.
- Contradictions and uncertainty were preserved.
- [[index]] reflects durable page changes.
- [[log]] records what changed and why.
