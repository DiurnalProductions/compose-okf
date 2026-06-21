---
id: compose.launched_effect
type: concept
title: LaunchedEffect
description: Launch a coroutine scoped to composition, cancelled on leave or key change.
tags: [compose, side-effects, coroutines]
prerequisites:
  - compose.effect_lifecycle_model
  - kotlin.coroutines
related:
  - compose.remember_coroutine_scope
  - compose.disposable_effect
  - compose.repository_integration
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`LaunchedEffect(key)` starts a coroutine when entering composition or when keys change. The coroutine cancels when keys change or the composable leaves the tree. Use for suspend work tied to UI presence.

# Mental model

Bind async work to a composable's lifetime. Keys are the restart contract — same keys mean continue; different keys mean cancel and relaunch.

# Example

```kotlin
LaunchedEffect(productId) {
    val details = repository.loadProduct(productId)
    uiState.value = details
}
```

# Common mistakes

- Using `LaunchedEffect(Unit)` for work that should restart on data changes
- Updating non-Compose mutable state without considering thread safety
- Long-running work without structured cancellation handling
- Using LaunchedEffect for one-shot events better handled by callbacks

# Related concepts

- [Remember Coroutine Scope](/concepts/remember_coroutine_scope.md)
- [Disposable Effect](/concepts/disposable_effect.md)
- [Repository Integration](/concepts/repository_integration.md)
