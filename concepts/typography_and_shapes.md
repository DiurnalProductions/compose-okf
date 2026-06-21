---
id: compose.typography_and_shapes
type: concept
title: Typography and Shapes
description: Material theme text styles and corner shape definitions.
tags: [compose, material, typography, shapes]
prerequisites:
  - compose.material_3
related:
  - compose.composition_locals
  - compose.dynamic_color
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Typography defines text styles (display, headline, body, label). Shapes define corner radii for components (small, medium, large). Both propagate via MaterialTheme composition locals.

# Mental model

Design tokens for text and corners — not per-Text font sizes. Use `MaterialTheme.typography.bodyLarge` and shape tokens for cohesive UI.

# Example

```kotlin
Text(
    "Headline",
    style = MaterialTheme.typography.headlineMedium,
)
Card(shape = MaterialTheme.shapes.medium) { /* ... */ }
```

# Common mistakes

- Arbitrary TextStyle on every Text composable
- Shape tokens ignored for custom components
- Typography not adjusted for accessibility scaling
- Hardcoded corner radius duplicating theme shapes

# Related concepts

- [Composition Locals](/concepts/composition_locals.md)
- [Dynamic Color](/concepts/dynamic_color.md)
