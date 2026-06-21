---
id: compose.ui_tree_vs_composition_tree
type: concept
title: UI Tree vs Composition Tree
description: Relationship between composition, layout, and draw phases.
tags: [compose, runtime, layout, draw]
prerequisites:
  - compose.recomposition_model
  - compose.compose_compiler_plugin
related:
  - compose.snapshot_system
  - compose.layout_vs_drawing_modifiers
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

The composition tree records composable call structure and state. Layout nodes measure and place. Draw passes render. Recomposition updates composition; layout and draw may be invalidated separately.

# Mental model

Three related trees/phases: **Compose** (what exists), **Layout** (how big/where), **Draw** (pixels). Not every recomposition relayouts or redraws everything — invalidation is scoped.

# Example

```kotlin
// State change may recompose Text without relayout if size unchanged
val color by animateColorAsState(targetColor)
Text("Hello", color = color)
```

# Common mistakes

- Conflating composition with layout size
- Assuming every state change repaints entire screen
- Debugging only composition while ignoring layout invalidation
- View-system analogies mapping 1:1 to Compose trees

# Related concepts

- [Snapshot System](/concepts/snapshot_system.md)
- [Layout Vs Drawing Modifiers](/concepts/layout_vs_drawing_modifiers.md)
