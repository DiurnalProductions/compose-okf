---
id: compose.spring_vs_tween
type: concept
title: Spring vs Tween Models
description: Physics-based springs versus timed easing interpolators for animations.
tags: [compose, animation, spring, tween]
prerequisites:
  - compose.animate_apis
related:
  - compose.state_driven_animation
  - compose.transition_apis
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Springs simulate physical motion with stiffness and damping — natural for gestures and interruptions. Tweens animate over fixed duration with easing curves — predictable for fades and timed transitions.

# Mental model

Springs can change target mid-flight smoothly. Tweens run clock-driven from start to end. Choose springs for interactive UI; tweens for declarative timed effects.

# Example

```kotlin
animateFloatAsState(
    targetValue = target,
    animationSpec = spring(dampingRatio = Spring.DampingRatioMediumBouncy),
)

animateFloatAsState(
    targetValue = target,
    animationSpec = tween(durationMillis = 300, easing = FastOutSlowInEasing),
)
```

# Common mistakes

- Using tween for drag-follow interactions that should spring
- Over-damped springs that feel sluggish
- Ignoring interruption behavior when targets change rapidly
- Matching unrelated properties with incompatible specs

# Related concepts

- [State Driven Animation](/concepts/state_driven_animation.md)
- [Transition Apis](/concepts/transition_apis.md)
