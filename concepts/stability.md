---
id: compose.stability
type: concept
title: Stability
description: Compose's classification of types whose equality implies substitutability for skipping.
tags: [compose, performance, recomposition]
prerequisites:
  - compose.recomposition_model
related:
  - compose.skippable_recompositions
  - compose.compose_compiler_plugin
  - compose.performance_pitfalls
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

A type is stable if Compose can determine that equal values produce equivalent UI behavior. Primitives, stable collections, and `@Stable`/`@Immutable` types enable skipping. Unstable types force recomposition.

# Mental model

Stability is a contract about predictability. If Compose cannot prove stability, it conservatively re-runs composables. Mark domain models `@Immutable` when fields are val and deeply immutable.

# Example

```kotlin
@Immutable
data class User(val id: String, val name: String)

@Composable
fun UserRow(user: User) {  // stable parameter enables skipping
    Text(user.name)
}
```

# Common mistakes

- Marking mutable classes as `@Immutable`
- Passing mutable lists that change identity every recomposition
- Assuming data classes are automatically stable
- Ignoring stability warnings from the Compose compiler

# Related concepts

- [Skippable Recompositions](/concepts/skippable_recompositions.md)
- [Compose Compiler Plugin](/concepts/compose_compiler_plugin.md)
- [Performance Pitfalls](/concepts/performance_pitfalls.md)
