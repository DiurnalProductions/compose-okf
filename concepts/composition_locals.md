---
id: compose.composition_locals
type: concept
title: Composition Locals
description: Implicit context propagation through the composable tree.
tags: [compose, theming, locals]
prerequisites:
  - compose.composable_functions
  - compose.remember
related:
  - compose.material_3
  - compose.typography_and_shapes
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`CompositionLocal` provides values implicitly to descendant composables without explicit parameters. Used for theming (`LocalContentColor`), density, lifecycle owner, and custom app context.

# Mental model

Scoped dynamic binding — like thread-local for UI tree. Providers override values for subtrees. Prefer explicit parameters for business data; locals for cross-cutting ambient context.

# Example

```kotlin
CompositionLocalProvider(LocalContentColor provides Color.White) {
    Text("On dark background")
}
```

# Common mistakes

- Overusing locals for data that should be explicit parameters
- Providing unstable values causing broad recomposition
- Reading locals in domain layers
- Custom locals without default factory values

# Related concepts

- [Material 3](/concepts/material_3.md)
- [Typography And Shapes](/concepts/typography_and_shapes.md)
