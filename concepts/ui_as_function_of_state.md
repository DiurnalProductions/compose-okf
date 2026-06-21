---
id: compose.ui_as_function_of_state
type: concept
title: UI as a Function of State
description: Compose UI is derived by executing composables against current observable state.
tags: [compose, declarative, state]
prerequisites:
  - compose.composable_functions
related:
  - compose.recomposition_model
  - compose.mutable_state_of
  - compose.unidirectional_data_flow
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

In Compose, UI is not updated imperatively. Instead, composables read state and emit UI that reflects the current values. When state changes, Compose re-executes affected composables to produce a new UI description.

# Mental model

UI = f(state). You declare what the screen should look like for any given state. You never call `setText` or `show()` — you change state and let recomposition rebuild the relevant UI. The UI tree is **rebuilt**, not mutated.

# Example

```kotlin
@Composable
fun Counter(count: Int, onIncrement: () -> Unit) {
    Column {
        Text("Count: $count")
        Button(onClick = onIncrement) { Text("Increment") }
    }
}
```

# Common mistakes

- Storing duplicate UI state alongside source-of-truth state
- Manually syncing UI widgets when state changes
- Mutating UI directly instead of updating state
- Assuming the composable body runs only once

# Related concepts

- [Recomposition Model](/concepts/recomposition_model.md)
- [Mutable State Of](/concepts/mutable_state_of.md)
- [Unidirectional Data Flow](/concepts/unidirectional_data_flow.md)
