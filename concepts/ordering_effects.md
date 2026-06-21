---
id: compose.ordering_effects
type: concept
title: Ordering Effects
description: Why the sequence of modifiers in a chain changes behavior.
tags: [compose, modifiers, layout]
prerequisites:
  - compose.modifier_chaining
related:
  - compose.layout_vs_drawing_modifiers
  - compose.modifiers_affecting_layout
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Modifier order matters because each modifier wraps the previous. Padding before background differs from background before padding. Clickable area, clip shape, and size all depend on chain order.

# Mental model

Read modifier chains **outward-in** or **left-to-right** as wrapping layers. The first modifier in the chain is closest to the composable content; the last is outermost for layout and hit testing.

# Example

```kotlin
// Outer padding — background includes padded area visually if ordered this way:
Modifier.padding(8.dp).background(Color.Gray)

// Inner padding — background only behind content:
Modifier.background(Color.Gray).padding(8.dp)
```

# Common mistakes

- Assuming modifier order is commutative
- Placing `clip` after drawing that should be clipped
- Putting `clickable` outside padding when padded area should not click
- Debugging layout without reordering modifiers systematically

# Related concepts

- [Layout Vs Drawing Modifiers](/concepts/layout_vs_drawing_modifiers.md)
- [Modifiers Affecting Layout](/concepts/modifiers_affecting_layout.md)
