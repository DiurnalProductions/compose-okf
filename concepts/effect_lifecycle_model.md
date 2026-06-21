---
id: compose.effect_lifecycle_model
type: concept
title: Effect Lifecycle Model
description: When side effects run, restart, and dispose relative to composition.
tags: [compose, side-effects, lifecycle]
prerequisites:
  - compose.composable_functions
  - kotlin.coroutines
related:
  - compose.launched_effect
  - compose.disposable_effect
  - compose.side_effect
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Side effects in Compose must not live in composable bodies directly. Effect APIs tie work to composition lifecycle: enter, update, and leave. Effects restart when keys change and dispose when leaving the tree.

# Mental model

Composition describes UI; effects perform external work. Effects observe the same lifecycle as their call site — if the composable leaves composition, effects must clean up. Keys define effect identity across recompositions.

# Example

```kotlin
// Effect restarts when userId changes; cancels on leave
LaunchedEffect(userId) {
    loadProfile(userId)
}
```

# Common mistakes

- Performing network IO directly in composable function bodies
- Effects without keys that should restart on input change
- Effects with keys that change every recomposition (infinite restart)
- Assuming effect order across sibling composables is guaranteed

# Related concepts

- [Launched Effect](/concepts/launched_effect.md)
- [Disposable Effect](/concepts/disposable_effect.md)
- [Side Effect](/concepts/side_effect.md)
