---
id: compose.hoisting_state
type: concept
title: Hoisting State
description: Move state to the lowest common ancestor that needs read or write access.
tags: [compose, state, hoisting]
prerequisites:
  - compose.state_ownership
  - compose.composable_functions
related:
  - compose.state_hoisting_patterns
  - compose.unidirectional_data_flow
  - compose.state_vs_mutable_state
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

State hoisting lifts state out of a composable into its caller, making the original composable stateless and reusable. The stateless composable receives value plus `onValueChange` callback.

# Mental model

If two siblings must share state, hoist it to their parent. If only one composable needs it, keep it local. Hoisting converts implicit internal state into explicit function parameters — the hallmark of reusable Compose UI.

# Example

```kotlin
@Composable
fun StatefulField() {
    var text by remember { mutableStateOf("") }
    StatelessField(value = text, onValueChange = { text = it })
}

@Composable
fun StatelessField(value: String, onValueChange: (String) -> Unit) {
    TextField(value = value, onValueChange = onValueChange)
}
```

# Common mistakes

- Hoisting everything to the root composable unnecessarily
- Hoisting state that is truly private to one leaf
- Passing `MutableState` instead of value + callback
- Forgetting to hoist when siblings need synchronized state

# Related concepts

- [State Hoisting Patterns](/concepts/state_hoisting_patterns.md)
- [Unidirectional Data Flow](/concepts/unidirectional_data_flow.md)
- [State Vs Mutable State](/concepts/state_vs_mutable_state.md)
