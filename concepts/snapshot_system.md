---
id: compose.snapshot_system
type: concept
title: Snapshot System
description: Transactional model for reading and writing observable Compose state.
tags: [compose, runtime, state]
prerequisites:
  - compose.recomposition_triggers
  - compose.mutable_state_of
related:
  - compose.recomposition_model
  - compose.ui_tree_vs_composition_tree
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

The snapshot system wraps state reads and writes in transactional snapshots. Reads during composition see consistent state; writes apply atomically and notify observers. This enables thread-safe state propagation and batched updates.

# Mental model

Each composition reads from a snapshot view of the world. Writes create a new snapshot generation. Observers compare generations to decide what to invalidate — similar to software transactional memory for UI state.

# Example

```kotlin
// Multiple writes in one frame are batched
count.value = 1
count.value = 2  // observers typically see coalesced update
```

# Common mistakes

- Reading state outside composition without snapshot context
- Mutating Compose state from arbitrary threads without snapshot APIs
- Assuming each assignment causes an immediate synchronous recomposition
- Mixing Compose state with unsynchronized mutable globals

# Related concepts

- [Recomposition Model](/concepts/recomposition_model.md)
- [Ui Tree Vs Composition Tree](/concepts/ui_tree_vs_composition_tree.md)
