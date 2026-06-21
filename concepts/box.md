---
id: compose.box
type: concept
title: Box
description: Stacks children on top of each other with alignment control.
tags: [compose, layout, box]
prerequisites:
  - compose.composable_functions
related:
  - compose.column
  - compose.row
  - compose.constraint_layout
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`Box` overlays its children, aligning them within shared bounds. Useful for badges, floating action buttons, backgrounds, and layered UI.

# Mental model

A Z-stack of composables sharing the same layout box. Later children draw above earlier ones unless modifiers alter drawing order.

# Example

```kotlin
Box(contentAlignment = Alignment.BottomEnd) {
    Image(painter, contentDescription = null)
    Badge(modifier = Modifier.padding(8.dp))
}
```

# Common mistakes

- Expecting Box to arrange children linearly
- Forgetting that all children measure to Box constraints
- Using Box when ConstraintLayout would clarify complex overlaps
- Missing content alignment for centered overlays

# Related concepts

- [Column](/concepts/column.md)
- [Row](/concepts/row.md)
- [Constraint Layout](/concepts/constraint_layout.md)
