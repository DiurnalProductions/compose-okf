---
id: compose.disposable_effect
type: concept
title: DisposableEffect
description: Setup and teardown effect with onDispose cleanup.
tags: [compose, side-effects, lifecycle]
prerequisites:
  - compose.effect_lifecycle_model
  - compose.launched_effect
related:
  - compose.lifecycle_interactions
  - compose.remember_coroutine_scope
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`DisposableEffect(key)` runs on enter and when keys change, providing `onDispose` for cleanup. Ideal for registering listeners, observers, or lifecycle bindings.

# Mental model

Acquire on enter, release on leave or key change. Pairs naturally with Android lifecycle components and subscription APIs.

# Example

```kotlin
DisposableEffect(lifecycleOwner) {
    val observer = LifecycleEventObserver { _, event -> /* ... */ }
    lifecycleOwner.lifecycle.addObserver(observer)
    onDispose { lifecycleOwner.lifecycle.removeObserver(observer) }
}
```

# Common mistakes

- Missing onDispose leading to leaks
- Registering listeners in composable body instead of DisposableEffect
- Keys that change every recomposition causing register/dispose thrashing
- Combining unrelated setup in one DisposableEffect without clear keys

# Related concepts

- [Lifecycle Interactions](/concepts/lifecycle_interactions.md)
- [Remember Coroutine Scope](/concepts/remember_coroutine_scope.md)
