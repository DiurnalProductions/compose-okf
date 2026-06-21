---
id: compose.state_ownership
type: concept
title: State Ownership
description: Rules for which composable or layer creates, holds, and mutates state.
tags: [compose, state, architecture]
prerequisites:
  - compose.remember
  - compose.ui_as_function_of_state
related:
  - compose.hoisting_state
  - compose.state_hoisting_patterns
  - compose.mvvm_integration
resource: https://developer.android.com/jetpack/compose
timestamp: 2026-01-01
---

# Summary

Every piece of state has exactly one owner responsible for creation and mutation. Owners may be composables (local UI state), ViewModels (screen state), or repositories (domain data). Non-owners receive read-only state and event callbacks.

# Mental model

Draw a boundary around who is allowed to write. UI events bubble up as lambdas; state flows down as parameters. Multiple writers to the same state create bugs — assign ownership deliberately based on scope and lifecycle.

# Example

```kotlin
// Screen owner (ViewModel) holds state; composable renders it
@Composable
fun TodoScreen(viewModel: TodoViewModel) {
    val todos by viewModel.todos.collectAsState()
    TodoList(todos = todos, onToggle = viewModel::toggle)
}
```

# Common mistakes

- Duplicating the same state in ViewModel and composable
- Letting child composables mutate parent-owned state directly
- Choosing composable-local state for data that survives rotation
- Mixing UI state and business state without clear boundaries

# Related concepts

- [Hoisting State](/concepts/hoisting_state.md)
- [State Hoisting Patterns](/concepts/state_hoisting_patterns.md)
- [Mvvm Integration](/concepts/mvvm_integration.md)
