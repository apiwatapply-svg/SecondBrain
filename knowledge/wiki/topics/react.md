---
type: topic
status: active
created: 2026-06-27
updated: 2026-06-27
tags:
  - wiki/topic
  - react
source_count: 1
---

# React

## Overview

This topic covers React as the UI library used by the registered
[[wiki/projects/react-pos|React POS]] code project. It includes core React mental
models, hooks, state management, effects, React DOM APIs, Server Components, and
React Compiler notes from the official documentation collection.

## Key Concepts

- [[wiki/concepts/react-components]] - UI is organized as composable component
  functions and elements.
- [[wiki/concepts/react-hooks]] - Hooks expose React capabilities inside function
  components and custom hooks.
- [[wiki/concepts/react-state]] - State is render-scoped, queued, and structured
  to match the UI model.
- [[wiki/concepts/react-effects]] - Effects synchronize with external systems and
  should not replace ordinary rendering or event logic.
- [[wiki/concepts/react-server-components]] - Server-rendered component model for
  build-time or request-time execution outside the client bundle.
- [[wiki/concepts/react-compiler]] - Automatic memoization and optimization layer
  for React applications.

## Important Sources

- [[wiki/sources/react-19-official-docs]] - accepted collection of official
  React documentation pages captured on 2026-06-27.

## Current Synthesis

For application work in this workspace, React should be treated as a component
and hooks system first. Keep components pure, derive UI from props and state, use
events for direct user actions, and reserve Effects for synchronization with
systems outside React. For the React POS frontend, this implies modeling screens
as small components, keeping state close to where it is needed, and avoiding
Effect-driven state derivations unless an external API, browser primitive, or
subscription is involved.

React 19 adds important areas to track: Actions and form hooks, Server
Components, Server Functions, and React Compiler. These are useful but should be
adopted deliberately in a project context, especially where framework support or
build tooling affects stability.

## Open Questions

- Which React framework or bundler will the React POS frontend use?
- Should React POS adopt React Compiler immediately, or start without it and add
  it after the baseline app structure is stable?
