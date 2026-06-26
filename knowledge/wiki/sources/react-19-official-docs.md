---
type: source
status: active
created: 2026-06-27
updated: 2026-06-27
tags:
  - wiki/source
source_type: documentation-collection
source_url: https://react.dev/
raw_file: raw/sources/2026-06-27-react-19-docs.md
author: React team
source_count: 176
---

# React 19 Official Docs

## Source

- Raw collection note: [[raw/sources/2026-06-27-react-19-docs]]
- Raw collection folder: `knowledge/raw/sources/2026-06-27-react-19-docs/`
- Representative files:
  - [[raw/sources/2026-06-27-react-19-docs/Quick Start]]
  - [[raw/sources/2026-06-27-react-19-docs/React Compiler]]
  - [[raw/sources/2026-06-27-react-19-docs/Server Components]]
  - [[raw/sources/2026-06-27-react-19-docs/useActionState – React]]
- URL: https://react.dev/
- Author: React team
- Published: not captured in clipped files
- Captured: 2026-06-27

## Summary

- This collection contains 176 clipped Markdown pages from the official React
  documentation, covering learning guides, API references, React DOM APIs,
  Server Components, compiler configuration, directives, and lint rules.
- The learning docs emphasize building UIs as components, passing props,
  rendering lists and conditions, responding to events, and managing state.
- The hooks documentation covers state, refs, effects, context, reducers,
  transitions, optimistic updates, deferred values, and form-related hooks.
- The React 19 docs include Server Components and Server Functions guidance,
  with a warning that framework/bundler integration APIs may change across
  React 19 minor versions.
- The React Compiler docs describe automatic memoization and incremental
  adoption paths intended to reduce manual `useMemo`, `useCallback`, and
  `React.memo` usage.
- Several pages focus on avoiding unnecessary Effects, preserving component
  purity, and using lint rules to catch React-specific mistakes.

## Key Claims

- Claim: React applications are composed from components that encapsulate UI
  logic and markup.
  - Evidence: [[raw/sources/2026-06-27-react-19-docs/Quick Start]]
  - Related pages: [[wiki/concepts/react-components]], [[wiki/topics/react]]
- Claim: Hooks are the primary function-component API for state, effects,
  context, refs, transitions, and other React capabilities.
  - Evidence: [[raw/sources/2026-06-27-react-19-docs/Built-in React Hooks]]
  - Related pages: [[wiki/concepts/react-hooks]]
- Claim: React state behaves like a snapshot during render, and updates are
  queued rather than mutating existing render values.
  - Evidence: [[raw/sources/2026-06-27-react-19-docs/State as a Snapshot]],
    [[raw/sources/2026-06-27-react-19-docs/Queueing a Series of State Updates]]
  - Related pages: [[wiki/concepts/react-state]]
- Claim: Effects should synchronize components with external systems, and many
  data derivations or event responses do not need Effects.
  - Evidence: [[raw/sources/2026-06-27-react-19-docs/Synchronizing with Effects]],
    [[raw/sources/2026-06-27-react-19-docs/You Might Not Need an Effect]]
  - Related pages: [[wiki/concepts/react-effects]]
- Claim: React Server Components can render before bundling in a separate server
  environment, but framework and bundler support APIs are not yet semver-stable
  across React 19 minor versions.
  - Evidence: [[raw/sources/2026-06-27-react-19-docs/Server Components]]
  - Related pages: [[wiki/concepts/react-server-components]]
- Claim: React Compiler is positioned as an automatic optimization layer that
  can reduce the need for manual memoization primitives.
  - Evidence: [[raw/sources/2026-06-27-react-19-docs/React Compiler]]
  - Related pages: [[wiki/concepts/react-compiler]]

## Pages Created Or Updated

- [[wiki/topics/react]]
- [[wiki/projects/react-pos]]
- [[wiki/entities/react]]
- [[wiki/concepts/react-components]]
- [[wiki/concepts/react-hooks]]
- [[wiki/concepts/react-state]]
- [[wiki/concepts/react-effects]]
- [[wiki/concepts/react-server-components]]
- [[wiki/concepts/react-compiler]]

## Conflicts

- None known.

## Open Questions

- Should the vault later split this broad collection into per-section source
  briefs for React learning, React reference, React DOM, RSC, and React Compiler?

