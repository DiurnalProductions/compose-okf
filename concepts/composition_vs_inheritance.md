---
id: compose.composition_vs_inheritance
type: concept
title: Composition vs Inheritance
description: Compose builds complex UI by nesting composables rather than subclassing UI components.
tags: [compose, architecture, composition]
prerequisites:
  - compose.composable_functions
related:
  - compose.state_hoisting_patterns
  - compose.modifier_chaining
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Jetpack Compose favors composition over inheritance. Custom UI is built by combining existing composables and accepting content via lambda slots, not by extending base widget classes.

# Mental model

Instead of subclassing `TextView` to add an icon, you write a composable that calls `Row { Icon(); Text() }`. Reusable behavior is shared through function parameters, modifiers, and slot lambdas — not override chains.

# Example

```kotlin
@Composable
fun LabelWithIcon(
    icon: @Composable () -> Unit,
    label: @Composable () -> Unit,
) {
    Row(verticalAlignment = Alignment.CenterVertically) {
        icon()
        Spacer(Modifier.width(8.dp))
        label()
    }
}
```

# Common mistakes

- Designing deep widget inheritance hierarchies
- Hiding state inside non-reusable composables instead of parameterizing
- Overloading composables with boolean flags instead of slot parameters
- Copy-pasting layout code instead of extracting composables

# Related concepts

- [State Hoisting Patterns](/concepts/state_hoisting_patterns.md)
- [Modifier Chaining](/concepts/modifier_chaining.md)
