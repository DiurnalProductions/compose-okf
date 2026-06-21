---
id: compose.keys_and_identity
type: concept
title: Keys and Identity
description: How Compose tracks slot identity across recompositions and conditional UI.
tags: [compose, recomposition, identity]
prerequisites:
  - compose.recomposition_model
related:
  - compose.item_keys
  - compose.list_diffing
  - compose.remember
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Compose assigns identity to composition slots based on call order and explicit keys. Keys disambiguate composables when call order changes — critical for lists, animations, and conditional branches.

# Mental model

Think of slot positions in the composition tree. Without keys, identity follows source order. With keys, identity follows logical item identity — preserving state when items reorder.

# Example

```kotlin
@Composable
fun KeyedToggle(showA: Boolean) {
    if (showA) {
        key("A") { StatefulPanel() }
    } else {
        key("B") { StatefulPanel() }
    }
}
```

# Common mistakes

- Using list index as key when items reorder or insert
- Omitting keys in `AnimatedContent` target changes
- Using random keys that destroy state every recomposition
- Assuming composable function name provides identity

# Related concepts

- [Item Keys](/concepts/item_keys.md)
- [List Diffing](/concepts/list_diffing.md)
- [Remember](/concepts/remember.md)
