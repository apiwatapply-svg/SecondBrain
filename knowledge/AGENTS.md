# AGENTS.md

This file is the operating schema for the SecondBrain Obsidian vault. Treat the
vault as an LLM Wiki: raw sources are the immutable evidence layer, `wiki/` is
the maintained knowledge layer, and this file defines the conventions that keep
future agent sessions consistent.

## Git

- Repository: `https://github.com/apiwatapply-svg/SecondBrain.git`
- Default branch: `main`
- Initial commit message: `first commit`
- Obsidian app state is local by default and ignored via `.gitignore`.

## Core Model

- `raw/` is the source-of-truth layer. Do not rewrite raw source files unless the
  user explicitly asks for cleanup or redaction.
- `wiki/` is the LLM-maintained synthesis layer. Create and update these pages
  as sources are ingested and questions are answered.
- `index.md` is the content map. Read it first, and update it whenever wiki
  pages are added, renamed, retired, or materially changed.
- `log.md` is append-only chronology. Add an entry for every ingest, query that
  becomes durable, lint pass, schema change, or major maintenance action.
- `templates/` contains page shapes. Use them before inventing a new format.
- `operations/` contains repeatable workflows. Follow the relevant workflow
  before making large edits.

## Directory Contract

```text
raw/
  inbox/       New unprocessed captures.
  sources/     Immutable accepted source files.
  assets/      Downloaded images, PDFs, audio, and other attachments.

wiki/
  maps/        Hub pages and overviews.
  areas/       Long-running responsibilities or life domains.
  projects/    Time-bounded efforts with outcomes.
  topics/      Broad subject pages.
  concepts/    Reusable ideas and definitions.
  entities/    Organizations, products, tools, places, and named things.
  people/      Person pages when useful.
  sources/     LLM-written source briefs that point back to raw files.
  syntheses/   Cross-source arguments, comparisons, and evergreen summaries.
  questions/   Durable answers promoted from chat.

templates/     Markdown templates for each page type.
operations/    Agent workflows for ingest, query, lint, and promotion.
```

## Naming

- Use lowercase kebab-case filenames: `attention-mechanism.md`.
- Use stable names over clever names. Prefer `retrieval-augmented-generation.md`
  over `rag-thoughts.md` unless the acronym is the canonical name.
- Use Obsidian wikilinks for internal links: `[[wiki/concepts/compiled-knowledge]]`.
- If a page is renamed, update backlinks, `index.md`, and `log.md`.

## Frontmatter

Every generated wiki page should begin with YAML frontmatter:

```yaml
---
type: concept
status: seed
created: 2026-06-23
updated: 2026-06-23
tags:
  - wiki/concept
source_count: 0
---
```

Allowed `status` values:

- `seed` - useful starter page with limited evidence.
- `active` - current and supported by sources.
- `needs-review` - suspected stale, thin, contradictory, or poorly linked.
- `retired` - superseded but kept for history.

## Evidence Rules

- Do not present sourced claims as settled unless they are backed by a raw source
  or an existing wiki page that cites sources.
- Prefer citations as links to source briefs in `wiki/sources/`, and have source
  briefs point to the immutable raw file in `raw/sources/`.
- If a claim comes from memory or conversation, label it as conversation-derived
  and consider filing it under `wiki/questions/` or `wiki/syntheses/`.
- If evidence conflicts, preserve the contradiction. Do not smooth it away.

## YouTube Source Rules

When ingesting a YouTube video saved by Obsidian Web Clipper or supplied as a
YouTube URL:

- Pull the channel name from YouTube itself during processing, not only from the
  clipped filename or page title.
- Add `channel_name` to frontmatter on the accepted source note and the source
  brief. If available, also add `channel_url` and `video_id`.
- Use `source_type: youtube-video` for these source briefs.
- If network access or page metadata prevents verification, set
  `channel_name: needs-review`, preserve the YouTube URL, and add an open
  question in the source brief and `log.md`.

## Ingest Workflow

When the user says `ingest`, `injest`, asks to process raw files, or adds sources
to the vault, read these files before editing ingest outputs:

1. [[AGENTS]]
2. [[index]]
3. [[log]]
4. [[operations/ingest-source]]
5. The relevant source template, usually [[templates/source-brief]] or
   [[templates/youtube-video-source]]
6. Relevant existing pages under `wiki/`
7. The raw source itself

Then follow [[operations/ingest-source]] exactly.

Minimum ingest outputs:

1. A raw file in `raw/sources/` or a note documenting where the source lives.
2. A source brief in `wiki/sources/`.
3. Updates to relevant topic, concept, entity, person, area, project, or
   synthesis pages.
4. Updated `index.md`.
5. New `log.md` entry.

## Query Workflow

Follow [[operations/query-wiki]].

Default query behavior:

1. Read `index.md`.
2. Search/read relevant wiki pages.
3. Read raw sources only when the wiki evidence is thin, ambiguous, or contested.
4. Answer with citations to wiki pages and source briefs.
5. If the answer is reusable, create or update a page in `wiki/questions/` or
   `wiki/syntheses/`, then update `index.md` and `log.md`.

## Lint Workflow

Follow [[operations/lint-wiki]].

Periodic checks:

- Broken links.
- Orphan pages.
- Important uncreated concepts.
- Duplicate or near-duplicate pages.
- Stale pages with old `updated` dates.
- Contradictions that lack a synthesis note.
- Source briefs that do not connect to any topic or concept page.

## Editing Rules

- Keep page edits focused. Avoid rewriting a whole page when a small section
  update is enough.
- Preserve useful uncertainty. Use sections like `Open Questions` and
  `Conflicts` rather than forcing false closure.
- Update `updated:` whenever a page changes materially.
- Prefer short, linked pages over massive unstructured notes.
- Do not modify `.obsidian/` unless the user explicitly asks for Obsidian
  configuration changes.



