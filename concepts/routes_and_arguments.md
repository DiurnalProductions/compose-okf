---
id: compose.routes_and_arguments
type: concept
title: Routes and Arguments
description: Type-safe routes and parameters for navigation destinations.
tags: [compose, navigation, routes]
prerequisites:
  - compose.navigation_compose
  - kotlin.sealed_classes
related:
  - compose.back_stack_model
  - compose.mvvm_integration
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Routes identify destinations as strings or typed route objects. Arguments serialize into the back stack entry. Prefer IDs over parcelables; use Kotlin serialization or Navigation type-safe APIs.

# Mental model

Route + args = address of a screen. ViewModels receive args via SavedStateHandle. Composables stay dumb — load data based on ID args.

# Example

```kotlin
composable("detail/{itemId}") { backStackEntry ->
    val itemId = backStackEntry.arguments?.getString("itemId")
    DetailScreen(itemId = itemId)
}
```

# Common mistakes

- Non-serializable complex objects in route arguments
- Nullable arguments without validation
- Stringly-typed routes without centralized route definitions
- Deep link patterns not matching in-app routes

# Related concepts

- [Back Stack Model](/concepts/back_stack_model.md)
- [Mvvm Integration](/concepts/mvvm_integration.md)
