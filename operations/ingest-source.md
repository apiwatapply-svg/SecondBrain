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
3. Create a source brief from [[templates/source-brief]] in `wiki/sources/`. For YouTube videos, use [[templates/youtube-video-source]] instead.
4. Extract important entities, people, concepts, topics, projects, and areas.
5. Update existing wiki pages before creating duplicates.
6. Create new pages from templates when a concept is important enough to stand
   alone.
7. Record contradictions or uncertainty explicitly.
8. Update [[index]].
9. Append an entry to [[log]].

## YouTube Web Clipper Videos

When the source is a YouTube video from Obsidian Web Clipper, `youtube.com`, or
`youtu.be`:

1. Open or inspect the canonical YouTube URL during processing.
2. Pull the channel name from YouTube page metadata, visible page data, or a
   reliable YouTube metadata endpoint.
3. Add these frontmatter fields to the accepted source note and source brief:
   - `source_type: youtube-video`
   - `channel_name: <verified channel name>`
   - `channel_url: <channel URL when available>`
   - `video_id: <YouTube video id when available>`
4. Do not infer `channel_name` only from the clip title, filename, or transcript.
5. If the channel cannot be verified, use `channel_name: needs-review`, keep the
   source URL, add an `Open Questions` note, and mention the gap in [[log]].

## Quality Bar

- The source brief links to raw evidence or the original URL.
- All important new pages have frontmatter.
- The index lists new durable pages.
- The log records what changed and why.


