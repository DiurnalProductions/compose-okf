---
id: compose.remember_coroutine_scope
type: concept
title: rememberCoroutineScope
description: Obtain a coroutine scope bound to the composable's lifecycle for event handlers.
tags: [compose, coroutines, side-effects]
prerequisites:
  - compose.effect_lifecycle_model
  - compose.remember
related:
  - compose.launched_effect
  - compose.mvvm_integration
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`rememberCoroutineScope()` returns a scope cancelled when the composable leaves composition. Use it to launch coroutines from callbacks (clicks) where LaunchedEffect is not appropriate.

# Mental model

Event-driven coroutine launcher tied to UI lifetime. Unlike LaunchedEffect, you control exactly when coroutines start — typically in response to user actions.

# Example

```kotlin
val scope = rememberCoroutineScope()
Button(onClick = {
    scope.launch { snackbarHostState.showSnackbar("Saved") }
}) { Text("Save") }
```

# Common mistakes

- Using rememberCoroutineScope for work that should auto-start on composition
- Launching uncancelled global scope work from composables
- Long operations in click handlers without considering cancellation
- Confusing scope with ViewModelScope responsibilities

# Related concepts

- [Launched Effect](/concepts/launched_effect.md)
- [Mvvm Integration](/concepts/mvvm_integration.md)
