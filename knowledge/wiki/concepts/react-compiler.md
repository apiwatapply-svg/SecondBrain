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

# React Compiler

## Definition

React Compiler is React's automatic optimization system for handling
memoization, reducing the need for manual `useMemo`, `useCallback`, and
`React.memo` in supported code.

## Why It Matters

Manual memoization can add complexity and stale assumptions. React Compiler may
reduce that burden, but it should be introduced with attention to build tooling,
lint rules, and incremental adoption.

## Examples

- Use incremental adoption for an existing app instead of enabling compilation
  everywhere at once.
- Use compiler directives to control function-level compilation when needed.

## Related

- [[wiki/topics/react]]
- [[wiki/concepts/react-hooks]]

## Sources

- [[wiki/sources/react-19-official-docs]]
- [[raw/sources/2026-06-27-react-19-docs/React Compiler]]
- [[raw/sources/2026-06-27-react-19-docs/compilationMode – React]]
- [[raw/sources/2026-06-27-react-19-docs/Directives – React]]

## Open Questions

- Should the first React POS frontend setup include React Compiler, or defer it
  until core workflows are implemented?
