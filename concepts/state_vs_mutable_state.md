---
id: compose.state_vs_mutable_state
type: concept
title: State vs MutableState
description: Read-only State for down-propagation; MutableState for owners that mutate.
tags: [compose, state, api]
prerequisites:
  - compose.mutable_state_of
related:
  - compose.hoisting_state
  - compose.state_ownership
  - compose.derived_state
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`State<T>` exposes read-only access via `.value`. `MutableState<T>` adds mutation. Stateless child composables should accept `State<T>` or plain values plus event callbacks, not `MutableState`.

# Mental model

Downward data flow uses immutable interfaces. Only the owner holds the mutable handle. Children receive `State` or plain parameters — they observe but do not own mutation rights.

# Example

```kotlin
@Composable
fun Display(count: State<Int>) {
    Text("${count.value}")
}

@Composable
fun Owner() {
    val count = remember { mutableStateOf(0) }
    Display(count = count)
}
```

# Common mistakes

- Passing `MutableState` to leaf composables that should be stateless
- Exposing `.value` writes through public APIs
- Confusing `State` with Android `SavedState` or ViewModel state
- Using `by` delegation without understanding read/write visibility

# Related concepts

- [Hoisting State](/concepts/hoisting_state.md)
- [State Ownership](/concepts/state_ownership.md)
- [Derived State](/concepts/derived_state.md)
