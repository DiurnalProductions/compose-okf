---
id: compose.skippable_recompositions
type: concept
title: Skippable Recompositions
description: When Compose can skip re-executing a composable because inputs are unchanged.
tags: [compose, performance, recomposition]
prerequisites:
  - compose.stability
related:
  - compose.recomposition_triggers
  - compose.derived_state
  - compose.performance_pitfalls
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

If all parameters to a composable are stable and equal to the previous invocation, Compose may skip calling the function entirely. Skipping is the primary mechanism for keeping recomposition cheap at scale.

# Mental model

Each composable call site is a memoization point. Same stable inputs → skip re-execution. Changed or unstable inputs → run again. Design APIs to maximize skip opportunities.

# Example

```kotlin
@Composable
fun ExpensiveChild(data: ImmutableData) {
    // Skipped when `data` is stable and unchanged
    HeavyVisualization(data)
}
```

# Common mistakes

- Capturing changing values in unstable lambda parameters
- Inline object creation in parameter lists
- Assuming `@Composable` functions always run when parent runs
- Premature micro-optimization before measuring recomposition counts

# Related concepts

- [Recomposition Triggers](/concepts/recomposition_triggers.md)
- [Derived State](/concepts/derived_state.md)
- [Performance Pitfalls](/concepts/performance_pitfalls.md)
