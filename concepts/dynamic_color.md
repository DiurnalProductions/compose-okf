---
id: compose.dynamic_color
type: concept
title: Dynamic Color
description: System-derived color schemes from wallpaper on Android 12+.
tags: [compose, material, theming, color]
prerequisites:
  - compose.material_3
  - compose.composition_locals
related:
  - compose.typography_and_shapes
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Dynamic color generates Material color schemes from the user's wallpaper using tonal palettes. Use `dynamicLightColorScheme` / `dynamicDarkColorScheme` when supported, with static fallback.

# Mental model

ColorScheme becomes user-personalized ambient context. Still propagate through MaterialTheme — individual composables remain theme-aware.

# Example

```kotlin
val scheme = if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.S) {
    dynamicDarkColorScheme(context)
} else {
    darkColorScheme()
}
MaterialTheme(colorScheme = scheme) { Content() }
```

# Common mistakes

- Dynamic color on unsupported API without fallback
- Brand colors lost entirely instead of seeding dynamic scheme
- Contrast failures without accessibility review
- Bypassing MaterialTheme for critical semantic colors

# Related concepts

- [Typography And Shapes](/concepts/typography_and_shapes.md)
