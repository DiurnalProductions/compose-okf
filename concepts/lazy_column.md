---
id: compose.lazy_column
type: concept
title: LazyColumn
description: Vertically scrolling list that composes only visible items.
tags: [compose, lists, lazy, performance]
prerequisites:
  - compose.column
  - compose.recomposition_model
related:
  - compose.lazy_row
  - compose.item_keys
  - compose.list_diffing
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`LazyColumn` virtualizes vertical lists by composing and laying out only visible items plus a small buffer. Essential for large or unbounded datasets.

# Mental model

Not a Column with scroll — a window over data. Items enter and leave composition as you scroll. Off-screen items do not exist in the composition tree.

# Example

```kotlin
LazyColumn {
    items(messages, key = { it.id }) { message ->
        MessageRow(message)
    }
}
```

# Common mistakes

- Using Column with verticalScroll for large lists
- Nesting lazy lists with conflicting scroll orientations
- Forgetting keys for stateful items
- Putting non-lazy heavy content as LazyColumn header without bounds

# Related concepts

- [Lazy Row](/concepts/lazy_row.md)
- [Item Keys](/concepts/item_keys.md)
- [List Diffing](/concepts/list_diffing.md)
