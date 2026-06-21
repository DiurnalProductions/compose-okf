---
id: compose.performance_pitfalls
type: concept
title: Performance Pitfalls
description: Common Compose mistakes that cause excessive recomposition or jank.
tags: [compose, performance, recomposition]
prerequisites:
  - compose.skippable_recompositions
  - compose.list_diffing
  - compose.stability
related:
  - compose.derived_state
  - compose.lazy_column
  - compose.stability
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Performance issues usually stem from unstable parameters, unscoped state reads, heavy work in composables, non-lazy lists, and missing keys. Measure with Layout Inspector and recomposition counts before optimizing.

# Mental model

Compose is fast by default if you respect stability, hoist state, lazy-load lists, and scope derived calculations. Jank is almost always unnecessary recompositions or main-thread work in composition.

# Example

```kotlin
// Pitfall: creates new lambda every recomposition → unstable
// Fix: rememberUpdatedState or extract stable callback from ViewModel

// Pitfall: Column + verticalScroll for 10_000 items
// Fix: LazyColumn with keys
```

# Common mistakes

- Premature `@Composable` splitting without profiling
- Reading global state high in tree causing full-screen recomposition
- Sorting/filtering large collections during composition
- Disabling optimization based on folklore instead of measurement

# Related concepts

- [Derived State](/concepts/derived_state.md)
- [Lazy Column](/concepts/lazy_column.md)
- [Stability](/concepts/stability.md)
