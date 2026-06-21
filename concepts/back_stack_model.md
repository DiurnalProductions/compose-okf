---
id: compose.back_stack_model
type: concept
title: Back Stack Model
description: How Navigation Compose manages destination history and back behavior.
tags: [compose, navigation, back-stack]
prerequisites:
  - compose.navigation_compose
related:
  - compose.routes_and_arguments
  - compose.lifecycle_interactions
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

The back stack is a LIFO history of destinations. `navigate` pushes; `popBackStack` removes entries. Launch modes and `popUpTo` control stack clearing behavior for tasks like authentication flows.

# Mental model

Each entry maps to a composable destination with saved state. System back pops the stack. Single-activity apps rely entirely on this stack for screen history.

# Example

```kotlin
navController.navigate("login") {
    popUpTo("home") { inclusive = true }
}
```

# Common mistakes

- Unbounded stack growth from repeated navigate to same route
- Incorrect popUpTo breaking expected back behavior
- Assuming process death preserves full stack without saved state
- Mixing manual back handling with NavController inconsistently

# Related concepts

- [Routes And Arguments](/concepts/routes_and_arguments.md)
- [Lifecycle Interactions](/concepts/lifecycle_interactions.md)
