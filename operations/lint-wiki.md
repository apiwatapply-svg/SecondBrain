---
type: operation
status: active
created: 2026-06-23
updated: 2026-06-23
tags:
  - operation/lint
---

# Lint Wiki

Use this workflow after major ingest batches or when the graph feels messy.

## Checks

1. Broken wikilinks.
2. Orphan pages that nothing links to.
3. Duplicate or near-duplicate pages.
4. Pages without frontmatter.
5. Pages missing `created`, `updated`, `type`, `status`, or `tags`.
6. Stale pages with old `updated` dates.
7. Source briefs not connected to topics, concepts, or syntheses.
8. Concepts mentioned repeatedly but lacking pages.
9. Contradictions without a synthesis or open question.

## Outputs

- Create a report from [[templates/lint-report]] if the lint pass is substantial.
- Fix small mechanical issues directly.
- Update [[index]] and [[log]].
