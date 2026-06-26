---
type: log
status: active
created: 2026-06-23
updated: 2026-06-27
tags:
  - wiki/log
---

# Log

Append-only record of wiki activity. Keep headings parseable:

`## [YYYY-MM-DD] action | Title`

## [2026-06-23] schema | Initial LLM Wiki architecture

- Created the vault architecture for a general second brain based on Karpathy's
  LLM Wiki pattern.
- Added raw source, wiki, template, and operation layers.
- Expanded `AGENTS.md` into the operating schema for future agent sessions.
- Seeded the index with starter pages for the architecture itself.

## [2026-06-23] schema | YouTube channel metadata requirement

- Added a YouTube Web Clipper ingest rule requiring `channel_name` in
  frontmatter for accepted YouTube source notes and source briefs.
- Added [[templates/youtube-video-source]] for YouTube video source briefs.

## [2026-06-23] ingest | Karpathy LLM Wiki gist

- Accepted the Web Clipper capture as [[raw/sources/2026-06-23-karpathy-llm-wiki]].
- Updated [[wiki/sources/karpathy-llm-wiki-gist]] with the raw file link and key
  claims from the full clipped source.
- Confirmed this source is a GitHub Gist, not a YouTube video, so YouTube
  `channel_name` metadata does not apply.

## [2026-06-25] schema | Workspace root and knowledge vault split

- Moved the Obsidian/LLM Wiki vault into `knowledge/`.
- Created root workspace routing rules in `AGENTS.md`.

## [2026-06-27] ingest | React 19 official documentation collection

- Accepted 176 clipped official React documentation pages from root `raw/React19`
  into [[raw/sources/2026-06-27-react-19-docs]].
- Added a raw collection note for the accepted documentation folder.
- Created [[wiki/sources/react-19-official-docs]] as a collection-level source
  brief instead of one brief per clipped page.
- Created React knowledge seed pages: [[wiki/topics/react]],
  [[wiki/projects/react-pos]],
  [[wiki/entities/react]], [[wiki/concepts/react-components]],
  [[wiki/concepts/react-hooks]], [[wiki/concepts/react-state]],
  [[wiki/concepts/react-effects]], [[wiki/concepts/react-server-components]],
  and [[wiki/concepts/react-compiler]].
- Confirmed this source collection is official documentation, not a YouTube
  source, so YouTube `channel_name` metadata does not apply.



