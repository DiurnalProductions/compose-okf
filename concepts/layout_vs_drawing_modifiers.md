---
id: compose.layout_vs_drawing_modifiers
type: concept
title: Layout vs Drawing Modifiers
description: Modifiers participate in layout, draw, or semantics phases differently.
tags: [compose, modifiers, layout, drawing]
prerequisites:
  - compose.modifier_chaining
  - compose.ordering_effects
related:
  - compose.modifiers_affecting_layout
  - compose.semantics_modifiers
  - compose.ui_tree_vs_composition_tree
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Layout modifiers change measurement and placement. Drawing modifiers affect rendering (background, border, shadow). Some modifiers participate in multiple phases. Understanding phases clarifies ordering effects.

# Mental model

Compose layout nodes pass through measure → place → draw → semantics. Modifiers hook into specific phases. Size and padding affect measure; background affects draw; semantics modifiers expose accessibility info.

# Example

```kotlin
Modifier
    .size(100.dp)           // layout
    .background(Color.Blue) // draw
    .semantics { contentDescription = "Tile" }  // semantics
```

# Common mistakes

- Using draw modifiers expecting them to change layout size
- Applying shadow without clip when content should be shaped
- Ignoring semantics phase for interactive draw-only overlays
- Custom modifiers that measure incorrectly in wrap-content scenarios

# Related concepts

- [Modifiers Affecting Layout](/concepts/modifiers_affecting_layout.md)
- [Semantics Modifiers](/concepts/semantics_modifiers.md)
- [Ui Tree Vs Composition Tree](/concepts/ui_tree_vs_composition_tree.md)
