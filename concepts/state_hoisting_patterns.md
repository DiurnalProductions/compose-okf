---
id: compose.state_hoisting_patterns
type: concept
title: State Hoisting Patterns
description: Recurring patterns for hoisting UI, screen, and form state.
tags: [compose, architecture, hoisting]
prerequisites:
  - compose.hoisting_state
  - compose.state_ownership
related:
  - compose.unidirectional_data_flow
  - compose.mvvm_integration
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Common hoisting patterns include: stateless presentational composables, container composables that wire ViewModel state, and controlled components (value + onValueChange). Patterns scale from atoms to screens.

# Mental model

Separate **state holders** from **UI renderers**. Holders decide policy; renderers decide presentation. Hoist to the level matching lifecycle and reuse needs.

# Example

```kotlin
@Composable
fun SearchScreen(viewModel: SearchViewModel) {
    val query by viewModel.query.collectAsState()
    SearchBar(
        query = query,
        onQueryChange = viewModel::onQueryChange,
        onSearch = viewModel::search,
    )
}
```

# Common mistakes

- Hoisting to ViewModel when state is purely ephemeral UI (expanded/collapsed)
- Keeping form state local when it must survive process death
- Mixing hoisted and internal state for the same field
- Prop drilling excessive callbacks instead of grouping state

# Related concepts

- [Unidirectional Data Flow](/concepts/unidirectional_data_flow.md)
- [Mvvm Integration](/concepts/mvvm_integration.md)
