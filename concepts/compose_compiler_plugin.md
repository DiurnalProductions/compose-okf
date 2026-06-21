---
id: compose.compose_compiler_plugin
type: concept
title: Compose Compiler Plugin
description: Compile-time transformation of @Composable functions (conceptual overview).
tags: [compose, compiler, runtime]
prerequisites:
  - compose.composable_functions
  - compose.stability
related:
  - compose.ui_tree_vs_composition_tree
  - compose.skippable_recompositions
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

The Compose compiler plugin transforms `@Composable` functions to emit composition code using a slot table, tracks source information, and infers stability/skippability. It enables the runtime to manage recomposition efficiently.

# Mental model

At compile time, composable bodies become calls that read/write slots — not regular JVM bytecode flow. The plugin is what makes composables callable only from composables and enables skippability analysis.

# Example

```kotlin
// Source:
@Composable fun Example() { Text("Hi") }

// Conceptually lowered to composition calls managing slots and group boundaries
```

# Common mistakes

- Assuming composables are interpreted at runtime
- Ignoring compiler stability diagnostics
- Version mismatch between Compose BOM and compiler extension
- Expecting reflection to invoke composables normally

# Related concepts

- [Ui Tree Vs Composition Tree](/concepts/ui_tree_vs_composition_tree.md)
- [Skippable Recompositions](/concepts/skippable_recompositions.md)
