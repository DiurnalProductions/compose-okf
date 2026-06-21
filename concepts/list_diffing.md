---
id: compose.list_diffing
type: concept
title: List Diffing
description: How Compose compares list data to reuse item compositions.
tags: [compose, lists, diffing, performance]
prerequisites:
  - compose.item_keys
  - compose.lazy_column
related:
  - compose.skippable_recompositions
  - compose.performance_pitfalls
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

When list data changes, Compose uses keys and item equality to determine which item composables can move, reuse, or must be recreated. Proper diffing minimizes throwaway work.

# Mental model

Like RecyclerView's DiffUtil conceptually: old list → new list mapping. Stable keys let Compose relocate existing compositions instead of rebuilding from scratch.

# Example

```kotlin
// After filter changes, keyed items reuse composition where IDs match
val filtered = todos.filter { it.active }
LazyColumn {
    items(filtered, key = { it.id }) { TodoRow(it) }
}
```

# Common mistakes

- Replacing entire list instances unnecessarily each update
- Animating list changes without stable keys
- Assuming item content lambda identity drives diffing
- Large list updates on main thread blocking frame

# Related concepts

- [Skippable Recompositions](/concepts/skippable_recompositions.md)
- [Performance Pitfalls](/concepts/performance_pitfalls.md)
