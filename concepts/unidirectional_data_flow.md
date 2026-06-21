---
id: compose.unidirectional_data_flow
type: concept
title: Unidirectional Data Flow
description: Events flow up; state flows down through the composable tree.
tags: [compose, architecture, udf]
prerequisites:
  - compose.state_hoisting_patterns
  - compose.ui_as_function_of_state
related:
  - compose.mvvm_integration
  - compose.repository_integration
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

UDF in Compose means state descends as immutable data and events ascend as function calls. Single source of truth prevents conflicting mutations and simplifies debugging.

# Mental model

A loop: User event → state holder reduces event → new state → recomposition renders new UI. No sideways mutation between sibling composables.

# Example

```kotlin
@Composable
fun UdfCounter(count: Int, onIncrement: () -> Unit) {
    Column {
        Text("$count")
        Button(onClick = onIncrement) { Text("+") }
    }
}
```

# Common mistakes

- Siblings communicating by mutating shared mutable objects
- Bidirectional binding without explicit event callbacks
- Business logic embedded in click lambdas instead of state holders
- Multiple sources of truth for the same UI field

# Related concepts

- [Mvvm Integration](/concepts/mvvm_integration.md)
- [Repository Integration](/concepts/repository_integration.md)
