---
id: compose.navigation_compose
type: concept
title: Navigation Compose
description: Declarative navigation graph for composable destinations.
tags: [compose, navigation, android]
prerequisites:
  - compose.composable_functions
  - compose.remember
related:
  - compose.back_stack_model
  - compose.routes_and_arguments
  - compose.lifecycle_interactions
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Navigation Compose provides a `NavHost` that maps routes to composable destinations. It integrates with the Android back stack and supports typed arguments, deep links, and nested graphs.

# Mental model

Navigation is part of UI state: current destination is state. NavController mutates back stack; NavHost recomposes to show the active destination composable.

# Example

```kotlin
NavHost(navController, startDestination = "home") {
    composable("home") { HomeScreen(onNavigate = { navController.navigate("detail") }) }
    composable("detail") { DetailScreen() }
}
```

# Common mistakes

- Hardcoding NavController deep in leaf composables
- Navigating from ViewModel without UI event indirection
- Missing popUpTo configuration causing duplicate destinations
- Passing large objects via arguments instead of IDs

# Related concepts

- [Back Stack Model](/concepts/back_stack_model.md)
- [Routes And Arguments](/concepts/routes_and_arguments.md)
- [Lifecycle Interactions](/concepts/lifecycle_interactions.md)
