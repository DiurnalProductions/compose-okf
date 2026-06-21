---
id: compose.composable_functions
type: concept
title: Composable Functions
description: Functions annotated with @Composable that describe UI by calling other composables.
tags: [compose, composables, declarative]
prerequisites:
  - kotlin.functions
  - kotlin.lambdas
related:
  - compose.ui_as_function_of_state
  - compose.composition_vs_inheritance
  - compose.remember
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Composable functions are the fundamental building blocks of Jetpack Compose. They are ordinary Kotlin functions marked with `@Composable` that describe UI by invoking other composables. They are not UI objects — they are invoked repeatedly during recomposition to produce an updated UI tree.

# Mental model

Think of a composable as a **pure description function** that runs in a special Compose context. Each call emits UI nodes into a slot table. The function may run many times; it must not assume it runs only once. Composables transform parameters into UI structure — they do not return View objects or hold mutable UI references.

# Example

```kotlin
@Composable
fun Greeting(name: String) {
    Text(text = "Hello, $name")
}

@Composable
fun App() {
    Column {
        Greeting(name = "Compose")
        Greeting(name = "World")
    }
}
```

# Common mistakes

- Treating composables like constructors that create persistent UI objects
- Performing side effects directly inside composable bodies
- Using `return` to exit early in ways that break composition structure
- Calling composables from non-composable contexts without a Compose runtime

# Related concepts

- [Ui As Function Of State](/concepts/ui_as_function_of_state.md)
- [Composition Vs Inheritance](/concepts/composition_vs_inheritance.md)
- [Remember](/concepts/remember.md)
