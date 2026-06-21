---
id: compose.item_keys
type: concept
title: Item Keys
description: Stable identifiers for list items to preserve state and enable diffing.
tags: [compose, lists, keys, identity]
prerequisites:
  - compose.keys_and_identity
  - compose.lazy_column
related:
  - compose.list_diffing
  - compose.performance_pitfalls
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Lazy list APIs accept a `key` lambda mapping each item to a stable ID. Keys let Compose match items across list changes, preserving remembered state and enabling efficient animations.

# Mental model

Keys are primary keys for list rows. Index is identity only when the list is static. When items insert, delete, or reorder, keys preserve which composition slot belongs to which data item.

# Example

```kotlin
LazyColumn {
    items(
        items = todos,
        key = { todo -> todo.id },
    ) { todo ->
        TodoItem(todo)
    }
}
```

# Common mistakes

- Using list index as key when list mutates
- Non-unique keys across items
- Keys derived from display text that can collide
- Omitting keys for items with internal remembered state

# Related concepts

- [List Diffing](/concepts/list_diffing.md)
- [Performance Pitfalls](/concepts/performance_pitfalls.md)
