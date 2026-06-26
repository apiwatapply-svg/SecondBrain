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

# React Hooks

## Definition

React hooks are functions that let function components and custom hooks use
React capabilities such as state, effects, refs, context, reducers, transitions,
and external-store subscriptions.

## Why It Matters

Hooks are the main API surface for modern React application behavior. They also
come with rules: call them at the top level of components or custom hooks, keep
components pure, and use lint rules to catch dependency and ordering mistakes.

## Examples

- `useState` for local interactive state.
- `useReducer` for more structured state transitions.
- `useMemo` and `useCallback` for memoized values and functions when needed.
- `useActionState`, `useOptimistic`, and `useTransition` for action-driven or
  concurrent UI flows.

## Related

- [[wiki/concepts/react-state]]
- [[wiki/concepts/react-effects]]
- [[wiki/concepts/react-compiler]]

## Sources

- [[wiki/sources/react-19-official-docs]]
- [[raw/sources/2026-06-27-react-19-docs/Built-in React Hooks]]
- [[raw/sources/2026-06-27-react-19-docs/Rules of Hooks]]

## Open Questions

- Which hooks should become project-level conventions for forms, API calls, and
  POS transaction state?
