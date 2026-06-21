---
id: compose.semantics_modifiers
type: concept
title: Semantics Modifiers
description: Expose accessibility, testing, and UI-automation metadata.
tags: [compose, modifiers, accessibility, semantics]
prerequisites:
  - compose.modifier_chaining
related:
  - compose.layout_vs_drawing_modifiers
  - compose.composable_functions
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Semantics modifiers annotate UI with merged accessibility trees, content descriptions, custom actions, and test tags. They decouple visual presentation from how assistive technologies interpret UI.

# Mental model

Parallel to the visual tree, Compose builds a semantics tree. Modifiers publish properties that merge upward. Tests and TalkBack consume semantics, not pixels.

# Example

```kotlin
Icon(
    Icons.Default.Favorite,
    contentDescription = "Add to favorites",
    modifier = Modifier.semantics { role = Role.Button },
)
```

# Common mistakes

- Omitting content descriptions on meaningful icons
- Duplicating clickable semantics on nested elements
- Using visual text as the only accessibility label when context is missing
- Test tags on unstable nodes that reorder in lists

# Related concepts

- [Layout Vs Drawing Modifiers](/concepts/layout_vs_drawing_modifiers.md)
- [Composable Functions](/concepts/composable_functions.md)
