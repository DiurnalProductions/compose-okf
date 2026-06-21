---
id: compose.column
type: concept
title: Column
description: Vertically arranges child composables in sequence.
tags: [compose, layout, column]
prerequisites:
  - compose.composable_functions
related:
  - compose.row
  - compose.box
  - compose.modifiers_affecting_layout
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`Column` is a vertical linear layout composable. Children are measured and placed top-to-bottom (or bottom-to-top in reverse). It accepts arrangement, alignment, and modifier parameters.

# Mental model

A vertical stack of slots. Each child receives vertical constraints from remaining space. `Column` itself is a composable function — it does not create a persistent layout object.

# Example

```kotlin
Column(
    modifier = Modifier.fillMaxWidth().padding(16.dp),
    verticalArrangement = Arrangement.spacedBy(8.dp),
) {
    Text("Title")
    Text("Subtitle")
}
```

# Common mistakes

- Nesting deep Columns without considering scroll containers
- Using Column for horizontal arrangement (use Row)
- Forgetting that children default to wrap content vertically
- Applying weight without filling available height

# Related concepts

- [Row](/concepts/row.md)
- [Box](/concepts/box.md)
- [Modifiers Affecting Layout](/concepts/modifiers_affecting_layout.md)
