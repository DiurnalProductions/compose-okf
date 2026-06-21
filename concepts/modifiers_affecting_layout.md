---
id: compose.modifiers_affecting_layout
type: concept
title: Modifiers Affecting Layout
description: Size, padding, offset, and alignment modifiers in the measurement pass.
tags: [compose, layout, modifiers]
prerequisites:
  - compose.modifier_chaining
  - compose.column
related:
  - compose.intrinsic_measurements
  - compose.ordering_effects
  - compose.constraint_layout
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Layout-affecting modifiers constrain or transform how composables measure and place themselves and children: `size`, `fillMaxWidth`, `padding`, `weight`, `align`, and `offset`.

# Mental model

Parent passes constraints down; child returns measured size; parent places child. Modifiers intercept this pipeline. `weight` in Row/Column divides remaining space; `fillMaxSize` expands to constraints.

# Example

```kotlin
Row(Modifier.fillMaxWidth()) {
    Text("Label", Modifier.weight(1f))
    Text("Value")
}
```

# Common mistakes

- Using fillMaxSize inside scrollable children without bounded constraints
- Applying weight outside Row/Column scope
- Expecting offset to affect layout space (it typically does not)
- Double-padding by applying padding at every layer

# Related concepts

- [Intrinsic Measurements](/concepts/intrinsic_measurements.md)
- [Ordering Effects](/concepts/ordering_effects.md)
- [Constraint Layout](/concepts/constraint_layout.md)
