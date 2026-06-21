---
id: compose.recomposition_model
type: concept
title: Recomposition Model
description: How Compose selectively re-executes composables to refresh UI when state changes.
tags: [compose, recomposition, runtime]
prerequisites:
  - compose.ui_as_function_of_state
related:
  - compose.recomposition_triggers
  - compose.skippable_recompositions
  - compose.ui_tree_vs_composition_tree
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Recomposition is the process of re-invoking composable functions when their inputs change. Compose tracks which composables read which state and schedules targeted re-execution. Recomposition is frequent, expected, and cheap when scoped correctly.

# Mental model

Imagine a spreadsheet: when a cell (state) changes, only formulas (composables) that depend on it recalculate. Compose maintains a composition tree mapping call sites to UI slots. Recomposition **re-runs functions** to update slots — it does not patch individual View properties.

# Example

```kotlin
@Composable
fun NameDisplay(name: State<String>) {
    // Re-runs when name.value changes
    Text(text = name.value)
}
```

# Common mistakes

- Treating recomposition as a bug or failure mode
- Doing expensive work unconditionally in composable bodies
- Assuming composable call order maps 1:1 to persistent object identity
- Fighting recomposition with imperative caches outside `remember`

# Related concepts

- [Recomposition Triggers](/concepts/recomposition_triggers.md)
- [Skippable Recompositions](/concepts/skippable_recompositions.md)
- [Ui Tree Vs Composition Tree](/concepts/ui_tree_vs_composition_tree.md)
