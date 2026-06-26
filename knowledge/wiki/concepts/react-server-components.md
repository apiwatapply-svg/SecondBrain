---
type: concept
status: active
created: 2026-06-27
updated: 2026-06-27
tags:
  - wiki/concept
  - react
source_count: 1
---

# React Server Components

## Definition

React Server Components are components that render before bundling in an
environment separate from the client application or SSR server. They can run at
build time or per request through a server.

## Why It Matters

Server Components can keep server-only work and heavy dependencies out of the
client bundle. However, React 19 documentation notes that the APIs used by
frameworks and bundlers to implement Server Components may change between React
19 minor versions.

## Examples

- Rendering static content at build time without shipping markdown parsing
  libraries to the browser.
- Fetching server-only data before client hydration.

## Related

- [[wiki/topics/react]]
- [[wiki/concepts/react-components]]

## Sources

- [[wiki/sources/react-19-official-docs]]
- [[raw/sources/2026-06-27-react-19-docs/Server Components]]
- [[raw/sources/2026-06-27-react-19-docs/Server Functions]]

## Open Questions

- Will React POS use a framework with Server Components support, or a client
  SPA architecture?
