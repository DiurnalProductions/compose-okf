---
id: compose.remember
type: concept
title: remember
description: Caches a value across recompositions of the same composition location.
tags: [compose, state, remember]
prerequisites:
  - compose.composable_functions
  - compose.mutable_state_of
related:
  - compose.state_ownership
  - compose.derived_state
  - compose.remember_coroutine_scope
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`remember` stores a value in the composition tree so it survives recomposition but is discarded when the composable leaves the tree. It is essential for preserving state objects, calculations, and delegates.

# Mental model

Each composable call site has a memory slot. `remember` writes once (per key) and reads on subsequent recompositions. Without it, values would be recreated every recomposition — breaking state continuity.

# Example

```kotlin
@Composable
fun TimerDisplay() {
    val startTime = remember { System.currentTimeMillis() }
    Text("Started at $startTime")
}
```

# Common mistakes

- Using `remember` for data that should live in ViewModel or repository
- Forgetting keys when identity should reset on input change
- Storing non-stable objects without considering recomposition cost
- Expecting `remember` to survive process death (use `rememberSaveable`)

# Related concepts

- [State Ownership](/concepts/state_ownership.md)
- [Derived State](/concepts/derived_state.md)
- [Remember Coroutine Scope](/concepts/remember_coroutine_scope.md)
