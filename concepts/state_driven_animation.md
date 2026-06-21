---
id: compose.state_driven_animation
type: concept
title: State-Driven Animation
description: Animations as consequences of state changes, not imperative commands.
tags: [compose, animation, state]
prerequisites:
  - compose.animate_apis
  - compose.transition_apis
  - compose.ui_as_function_of_state
related:
  - compose.unidirectional_data_flow
  - compose.spring_vs_tween
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

In Compose, you animate by changing target state and letting animation APIs interpolate. UI reads animated state each frame. This aligns animation with the declarative model.

# Mental model

Don't call `animator.start()`. Set `expanded = true` and let `animate*AsState` or `Transition` handle frames. The animation **is** a series of recompositions with changing interpolated values.

# Example

```kotlin
var expanded by remember { mutableStateOf(false) }
val rotation by animateFloatAsState(if (expanded) 180f else 0f)

IconButton(onClick = { expanded = !expanded }) {
    Icon(Icons.Default.ArrowDropDown, null, Modifier.rotate(rotation))
}
```

# Common mistakes

- Imperative AnimationDrawable or ObjectAnimator patterns inside composables
- Mutating animation values directly bypassing state
- State and animated display state diverging
- Forgetting to use `animate*AsState` return value in UI

# Related concepts

- [Unidirectional Data Flow](/concepts/unidirectional_data_flow.md)
- [Spring Vs Tween](/concepts/spring_vs_tween.md)
