---
id: compose.repository_integration
type: concept
title: Repository Integration
description: Loading domain data into Compose UI through repositories and ViewModels.
tags: [compose, architecture, data]
prerequisites:
  - compose.mvvm_integration
  - kotlin.coroutines
related:
  - compose.launched_effect
  - compose.unidirectional_data_flow
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Repositories provide domain data; ViewModels orchestrate loading and expose UI state; composables render. Use coroutines in ViewModel scope — not composables — for repository calls.

# Mental model

Data layer is oblivious to Compose. ViewModel maps domain results to UI state models (`UiState`). Composables observe UiState and emit user intents upward.

# Example

```kotlin
class ItemsViewModel(private val repo: ItemRepository) : ViewModel() {
    val items = repo.observeItems()
        .stateIn(viewModelScope, SharingStarted.WhileSubscribed(5_000), emptyList())
}
```

# Common mistakes

- Calling repository directly from LaunchedEffect without ViewModel
- Mapping DTOs to UI in composables instead of ViewModel
- No loading/error state modeling in UiState
- Collecting cold flows in every recomposition

# Related concepts

- [Launched Effect](/concepts/launched_effect.md)
- [Unidirectional Data Flow](/concepts/unidirectional_data_flow.md)
