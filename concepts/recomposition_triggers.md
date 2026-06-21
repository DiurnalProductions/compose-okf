---
id: compose.recomposition_triggers
type: concept
title: Recomposition Triggers
description: Events that cause Compose to invalidate and re-run composables.
tags: [compose, recomposition, runtime]
prerequisites:
  - compose.recomposition_model
related:
  - compose.snapshot_system
  - compose.stability
  - compose.mutable_state_of
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Recomposition triggers include writes to observed `State`, changes to composable parameters, parent recomposition, and explicit invalidations. Compose schedules recomposition asynchronously and coalesces multiple state writes.

# Mental model

Reading state during composition registers a subscription. Writing state marks subscribers dirty. Parameter changes compare against previous invocation — unstable or changed parameters force child recomposition.

# Example

```kotlin
@Composable
fun TriggerDemo(flag: Boolean) {
    val color = if (flag) Color.Red else Color.Blue  // param change triggers recomposition
    Box(Modifier.background(color))
}
```

# Common mistakes

- Assuming only `State` writes trigger recomposition
- Creating new object instances as parameters every recomposition
- Using non-stable lambdas without `rememberUpdatedState` where needed
- Expecting synchronous immediate UI updates mid-composition

# Related concepts

- [Snapshot System](/concepts/snapshot_system.md)
- [Stability](/concepts/stability.md)
- [Mutable State Of](/concepts/mutable_state_of.md)
