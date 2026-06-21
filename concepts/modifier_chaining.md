---
id: compose.modifier_chaining
type: concept
title: Modifier Chaining
description: Compose modifiers as ordered, chained transformations on composables.
tags: [compose, modifiers, layout]
prerequisites:
  - compose.composable_functions
related:
  - compose.ordering_effects
  - compose.layout_vs_drawing_modifiers
  - compose.modifiers_affecting_layout
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Modifiers decorate composables with size, padding, input handling, drawing, and semantics. They chain via `Modifier.padding().clickable()` forming a single composed modifier applied to the layout node.

# Mental model

Modifiers are a functional pipeline: each modifier wraps the next. The chain is data — not a mutable object graph. Order determines whether padding is inside or outside a border, for example.

# Example

```kotlin
Text(
    "Hello",
    modifier = Modifier
        .fillMaxWidth()
        .padding(16.dp)
        .clickable { /* handle click */ },
)
```

# Common mistakes

- Creating new modifier chains inside unstable lambdas unnecessarily
- Using `Modifier` as a mutable field on a custom object
- Splitting chains inconsistently across wrappers
- Applying size modifiers in wrong order relative to padding

# Related concepts

- [Ordering Effects](/concepts/ordering_effects.md)
- [Layout Vs Drawing Modifiers](/concepts/layout_vs_drawing_modifiers.md)
- [Modifiers Affecting Layout](/concepts/modifiers_affecting_layout.md)
