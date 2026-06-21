---
id: compose.animate_apis
type: concept
title: Animate APIs
description: Functions like animateFloatAsState that interpolate values across frames.
tags: [compose, animation, animate]
prerequisites:
  - compose.mutable_state_of
  - compose.recomposition_model
related:
  - compose.spring_vs_tween
  - compose.transition_apis
  - compose.state_driven_animation
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Animate APIs (`animate*AsState`, `animateColorAsState`, etc.) smoothly transition a single value toward a target when state changes. They return `State` that updates each frame until the animation completes.

# Mental model

Target state changes → animation engine drives in-between values → composables recompose each frame with interpolated state. Animation is state-driven, not imperative `start()` calls on animator objects.

# Example

```kotlin
val size by animateDpAsState(
    targetValue = if (expanded) 200.dp else 100.dp,
    label = "size",
)
Box(Modifier.size(size))
```

# Common mistakes

- Creating new target values every frame causing restart loops
- Animating without `label` in newer Compose versions (debugging/tooling)
- Using animate APIs for multi-property coordinated transitions without Transition
- Running heavy logic inside animation target calculation

# Related concepts

- [Spring Vs Tween](/concepts/spring_vs_tween.md)
- [Transition Apis](/concepts/transition_apis.md)
- [State Driven Animation](/concepts/state_driven_animation.md)
