---
id: compose.lazy_row
type: concept
title: LazyRow
description: Horizontally scrolling lazy list of items.
tags: [compose, lists, lazy, performance]
prerequisites:
  - compose.row
  - compose.lazy_column
related:
  - compose.item_keys
  - compose.performance_pitfalls
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`LazyRow` is the horizontal counterpart to LazyColumn. It virtualizes item composition along the horizontal axis for carousels, chip rows, and timelines.

# Mental model

Same virtualization model as LazyColumn, rotated 90 degrees. Only visible horizontal items are composed.

# Example

```kotlin
LazyRow(horizontalArrangement = Arrangement.spacedBy(8.dp)) {
    items(tags, key = { it.id }) { tag ->
        TagChip(tag)
    }
}
```

# Common mistakes

- Using Row with horizontalScroll for many items
- Items without fixed or measurable widths causing measure loops
- Missing content padding for edge items
- Same key mistakes as LazyColumn

# Related concepts

- [Item Keys](/concepts/item_keys.md)
- [Performance Pitfalls](/concepts/performance_pitfalls.md)
