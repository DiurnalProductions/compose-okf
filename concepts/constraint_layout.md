---
id: compose.constraint_layout
type: concept
title: Constraint Layout
description: Constraint-based layout for complex relationships between composables.
tags: [compose, layout, constraints]
prerequisites:
  - compose.column
  - compose.row
  - compose.box
related:
  - compose.modifiers_affecting_layout
  - compose.intrinsic_measurements
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

ConstraintLayout (Compose) positions children using constraints relative to siblings or the parent — similar to ConstraintLayout in the View system but declarative. Ideal for responsive layouts with many interdependent positions.

# Mental model

Define a graph of positional rules: edges pinned to parent or other composables, chains, barriers, and guidelines. The solver computes final positions from constraints rather than sequential flow.

# Example

```kotlin
ConstraintLayout(modifier = Modifier.fillMaxSize()) {
    val (title, action) = createRefs()
    Text("Title", Modifier.constrainAs(title) {
        top.linkTo(parent.top)
        start.linkTo(parent.start)
    })
    Button(onClick = {}, Modifier.constrainAs(action) {
        end.linkTo(parent.end)
        centerVerticallyTo(title)
    }) { Text("Go") }
}
```

# Common mistakes

- Using ConstraintLayout for simple linear layouts
- Creating over-constrained or circular constraint dependencies
- Ignoring performance cost of complex constraint graphs
- Mixing flow layouts and constraints without clear hierarchy

# Related concepts

- [Modifiers Affecting Layout](/concepts/modifiers_affecting_layout.md)
- [Intrinsic Measurements](/concepts/intrinsic_measurements.md)
