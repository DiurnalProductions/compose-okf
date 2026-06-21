---
id: compose.row
type: concept
title: Row
description: Horizontally arranges child composables in sequence.
tags: [compose, layout, row]
prerequisites:
  - compose.composable_functions
related:
  - compose.column
  - compose.box
  - compose.modifiers_affecting_layout
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`Row` lays out children horizontally left-to-right (or right-to-left in RTL). It mirrors `Column` with horizontal arrangement and vertical alignment controls.

# Mental model

Horizontal counterpart to Column. Space is divided along the main axis; cross-axis alignment positions children vertically within the row height.

# Example

```kotlin
Row(
    horizontalArrangement = Arrangement.SpaceBetween,
    verticalAlignment = Alignment.CenterVertically,
) {
    Icon(Icons.Default.Star, contentDescription = null)
    Text("Rated")
}
```

# Common mistakes

- Putting unbounded-width content in Row without weight or scroll
- Using Row when Column would simplify vertical forms
- Ignoring RTL layout direction
- Overflows when too many children lack flexible sizing

# Related concepts

- [Column](/concepts/column.md)
- [Box](/concepts/box.md)
- [Modifiers Affecting Layout](/concepts/modifiers_affecting_layout.md)
