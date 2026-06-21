---
id: compose.derived_state
type: concept
title: Derived State
description: Compute UI values from other state with automatic invalidation.
tags: [compose, state, performance]
prerequisites:
  - compose.remember
  - compose.mutable_state_of
related:
  - compose.stability
  - compose.skippable_recompositions
  - compose.performance_pitfalls
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Derived state transforms source state into values ready for UI. Use `derivedStateOf` to recalculate only when upstream state changes affect the derived result, reducing unnecessary recompositions.

# Mental model

Like a spreadsheet formula cell. Source states are inputs; derived state is the computed output. Compose tracks dependencies so the derivation re-runs only when inputs change in ways that matter.

# Example

```kotlin
@Composable
fun FilteredList(items: List<String>, query: String) {
    val filtered by remember {
        derivedStateOf { items.filter { it.contains(query, ignoreCase = true) } }
    }
    LazyColumn {
        items(filtered) { item -> Text(item) }
    }
}
```

# Common mistakes

- Filtering or sorting large lists on every recomposition without `derivedStateOf`
- Using derived state for expensive IO or network work
- Deriving state that should be computed in ViewModel/domain layer
- Creating derived state outside `remember` so it resets each recomposition

# Related concepts

- [Stability](/concepts/stability.md)
- [Skippable Recompositions](/concepts/skippable_recompositions.md)
- [Performance Pitfalls](/concepts/performance_pitfalls.md)
