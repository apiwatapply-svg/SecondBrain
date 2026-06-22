# SecondBrain

This vault is a local-first second brain built around the LLM Wiki pattern:

1. Curate raw sources.
2. Let the LLM compile them into durable, linked wiki pages.
3. Use Obsidian as the human browsing and review environment.
4. Keep the system honest with an explicit schema, index, log, and lint workflow.

Start here:

- [[index]] - content map and active entry points.
- [[log]] - chronological record of ingests, queries, and maintenance.
- [[operations/ingest-source]] - how to process a new source.
- [[operations/query-wiki]] - how to answer questions from the wiki.
- [[operations/lint-wiki]] - how to health-check the graph.

The source idea is Karpathy's LLM Wiki pattern:
https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
