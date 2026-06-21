---
id: compose.mvvm_integration
type: concept
title: MVVM Integration
description: Connecting ViewModels to composables for screen-level state.
tags: [compose, architecture, mvvm, viewmodel]
prerequisites:
  - compose.unidirectional_data_flow
  - compose.composable_functions
related:
  - compose.repository_integration
  - compose.state_ownership
  - compose.launched_effect
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

ViewModels expose UI state as flows or snapshot state collected in composables via `collectAsStateWithLifecycle`. ViewModels survive configuration changes; composables remain declarative renderers.

# Mental model

ViewModel = state holder + event handler at screen scope. Composable = pure function of ViewModel state. Navigation and process death may require SavedStateHandle integration.

# Example

```kotlin
@Composable
fun ProfileScreen(viewModel: ProfileViewModel = hiltViewModel()) {
    val uiState by viewModel.uiState.collectAsStateWithLifecycle()
    ProfileContent(state = uiState, onAction = viewModel::handleAction)
}
```

# Common mistakes

- Holding Context or View references in ViewModel
- Collecting flows without lifecycle awareness
- Exposing MutableState directly from ViewModel instead of StateFlow
- Putting Android framework types in domain layers

# Related concepts

- [Repository Integration](/concepts/repository_integration.md)
- [State Ownership](/concepts/state_ownership.md)
- [Launched Effect](/concepts/launched_effect.md)
