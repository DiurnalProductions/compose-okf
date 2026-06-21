---
id: compose.material_3
type: concept
title: Material 3
description: Material Design 3 components and theming in Compose.
tags: [compose, material, theming, m3]
prerequisites:
  - compose.composition_locals
related:
  - compose.dynamic_color
  - compose.typography_and_shapes
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Material 3 (`MaterialTheme`) supplies color scheme, typography, and shapes to Material composables. Wrap app content in `MaterialTheme` to apply consistent design tokens.

# Mental model

MaterialTheme installs composition locals consumed by `Button`, `Text`, `Card`, etc. Components read tokens — you customize tokens, not each widget individually.

# Example

```kotlin
MaterialTheme(
    colorScheme = lightColorScheme(),
    typography = Typography(),
) {
    Surface { AppContent() }
}
```

# Common mistakes

- Hardcoding colors on Material components bypassing theme
- Mixing Material 2 and Material 3 components inconsistently
- Missing MaterialTheme wrapper in previews
- Custom components not reading theme locals

# Related concepts

- [Dynamic Color](/concepts/dynamic_color.md)
- [Typography And Shapes](/concepts/typography_and_shapes.md)
