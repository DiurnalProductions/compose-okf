---
id: compose.side_effect
type: concept
title: SideEffect
description: Publish Compose state to non-Compose code after every successful composition.
tags: [compose, side-effects]
prerequisites:
  - compose.effect_lifecycle_model
related:
  - compose.launched_effect
  - compose.disposable_effect
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`SideEffect` runs after composition completes, on every recomposition. Use it to sync Compose state to external objects (analytics, legacy listeners) without restarting coroutines.

# Mental model

A post-composition hook. Unlike LaunchedEffect, it does not launch coroutines and does not use keys for cancellation — it fires after each successful commit.

# Example

```kotlin
SideEffect {
    analyticsTracker.setScreenName(screenName)
}
```

# Common mistakes

- Heavy work in SideEffect blocking the frame
- Using SideEffect where LaunchedEffect with keys is appropriate
- Mutating Compose state inside SideEffect causing recomposition loops
- Assuming SideEffect runs before layout/draw

# Related concepts

- [Launched Effect](/concepts/launched_effect.md)
- [Disposable Effect](/concepts/disposable_effect.md)
