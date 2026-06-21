---
id: compose.mutable_state_of
type: concept
title: mutableStateOf
description: Creates observable mutable state that triggers recomposition when values change.
tags: [compose, state, mutableStateOf]
prerequisites:
  - compose.ui_as_function_of_state
related:
  - compose.state_vs_mutable_state
  - compose.remember
  - compose.snapshot_system
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`mutableStateOf` wraps a value in Compose's observable state system. Reads during composition establish dependencies; writes schedule recomposition of affected composables.

# Mental model

A `MutableState` is a reactive cell. Composables that read `.value` subscribe to it. Assignment to `.value` publishes a change through the snapshot system, which invalidates dependent compositions.

# Example

```kotlin
@Composable
fun ClickCounter() {
    val count = remember { mutableStateOf(0) }
    Button(onClick = { count.value++ }) {
        Text("Clicked ${count.value} times")
    }
}
```

# Common mistakes

- Mutating objects inside state without replacing or using mutable state wrappers
- Creating `mutableStateOf` on every recomposition without `remember`
- Using mutable state for values that should be derived
- Holding large unrelated objects in a single state holder

# Related concepts

- [State Vs Mutable State](/concepts/state_vs_mutable_state.md)
- [Remember](/concepts/remember.md)
- [Snapshot System](/concepts/snapshot_system.md)
