---
id: compose.transition_apis
type: concept
title: Transition APIs
description: Coordinate multiple animations across discrete UI states.
tags: [compose, animation, transition]
prerequisites:
  - compose.animate_apis
related:
  - compose.state_driven_animation
  - compose.keys_and_identity
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

`Transition`, `updateTransition`, and `AnimatedVisibility` animate several properties together between discrete states. They provide child animations scoped to a shared transition lifecycle.

# Mental model

Define states (often sealed class or boolean). Transition tracks current vs target state and exposes animated values for each property. Enter/exit can use separate specs.

# Example

```kotlin
AnimatedVisibility(visible = expanded) {
    ExpandedContent()
}
```

# Common mistakes

- Independent animate* calls that should be synchronized in Transition
- Missing keys causing enter/exit animation glitches
- Nesting too many AnimatedVisibility layers
- Transition state stored separately from UI source-of-truth

# Related concepts

- [State Driven Animation](/concepts/state_driven_animation.md)
- [Keys And Identity](/concepts/keys_and_identity.md)
