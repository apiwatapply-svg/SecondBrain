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

# React State

## Definition

React state is component memory that participates in rendering. Each render sees
a snapshot of state, and state updates are queued for React to process rather
than applied as direct mutations to the current render.

## Why It Matters

POS interfaces depend on predictable transaction state. Cart contents, selected
customer, active terminal, discounts, and payment state should be modeled so the
UI can be derived from state consistently.

## Examples

- Keep related state together when it changes together.
- Avoid duplicated state that can be derived from props or existing state.
- Use reducers when state transitions become easier to reason about as named
  actions.

## Related

- [[wiki/concepts/react-components]]
- [[wiki/concepts/react-hooks]]
- [[wiki/concepts/react-effects]]

## Sources

- [[wiki/sources/react-19-official-docs]]
- [[raw/sources/2026-06-27-react-19-docs/State as a Snapshot]]
- [[raw/sources/2026-06-27-react-19-docs/Queueing a Series of State Updates]]
- [[raw/sources/2026-06-27-react-19-docs/Choosing the State Structure]]

## Open Questions

- Should React POS cart state start as component-local state, context, reducer,
  or an external store?
