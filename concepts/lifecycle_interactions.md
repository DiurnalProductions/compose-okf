---
id: compose.lifecycle_interactions
type: concept
title: Lifecycle Interactions
description: How navigation and composition align with Android lifecycle events.
tags: [compose, navigation, lifecycle]
prerequisites:
  - compose.navigation_compose
  - compose.disposable_effect
related:
  - compose.effect_lifecycle_model
  - compose.mvvm_integration
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

When destinations change, composables enter and leave composition, triggering effect disposal. Collect flows with lifecycle-aware APIs. ViewModels outlive composables but respect cleared scope when back stack entries are removed.

# Mental model

Composition lifetime ⊆ destination lifetime ⊆ activity lifetime. DisposableEffect bridges Compose to Android lifecycle owners. Navigation pop removes destination composition.

# Example

```kotlin
val lifecycle = LocalLifecycleOwner.current.lifecycle
val state by flow.collectAsStateWithLifecycle(
    lifecycle = lifecycle,
    minActiveState = Lifecycle.State.STARTED,
)
```

# Common mistakes

- Collecting flows when STOPPED wasting resources
- Assuming ViewModel clears when composable disposes (it may persist)
- Listeners registered in composable body without disposal
- Ignoring process death vs configuration change distinctions

# Related concepts

- [Effect Lifecycle Model](/concepts/effect_lifecycle_model.md)
- [Mvvm Integration](/concepts/mvvm_integration.md)
