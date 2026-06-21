---
id: compose.intrinsic_measurements
type: concept
title: Intrinsic Measurements
description: Querying composables for size preferences before final layout.
tags: [compose, layout, measurement]
prerequisites:
  - compose.modifiers_affecting_layout
related:
  - compose.column
  - compose.row
  - compose.constraint_layout
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Intrinsic measurement APIs let layouts ask children how large they would like to be along an axis (min, max, exact). Useful for custom layouts and adaptive sizing.

# Mental model

Before committing to final constraints, a parent can probe: 'how wide would you be if height were X?' Intrinsic queries enable behaviors like wrapping content in toolbars or balanced rows.

# Example

```kotlin
// Row uses intrinsic height to align children with varying heights
Row(Modifier.height(IntrinsicSize.Min)) {
    Column(Modifier.weight(1f)) { /* ... */ }
    Divider(Modifier.fillMaxHeight().width(1.dp))
}
```

# Common mistakes

- Overusing intrinsic measurements in performance-critical lists
- Custom layouts that ignore intrinsic min/max queries
- Assuming intrinsic and final measure passes always agree
- Nested intrinsic layouts causing exponential measure passes

# Related concepts

- [Column](/concepts/column.md)
- [Row](/concepts/row.md)
- [Constraint Layout](/concepts/constraint_layout.md)
