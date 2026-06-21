# Jetpack Compose Knowledge Pack

> Jetpack Compose is a declarative UI system where UI is a function of state, and recomposition replaces mutation.

This OKF knowledge pack teaches Compose-native mental models: composables as functions, state-driven UI, explicit side effects, and performance through stability and scoped recomposition.

**External prerequisites:** [kotlin.functions](/../kotlin/concepts/functions.md), [kotlin.lambdas](/../kotlin/concepts/lambdas.md), [kotlin.coroutines](/../kotlin/concepts/coroutines.md), [kotlin.sealed_classes](/../kotlin/concepts/sealed_classes.md). Android lifecycle awareness is helpful but not required.

---

## Start Here

If you are new to Compose, read in this order:

1. [Composable Functions](/concepts/composable_functions.md) — UI as Kotlin functions, not objects
2. [UI as a Function of State](/concepts/ui_as_function_of_state.md) — the core declarative contract
3. [Composition vs Inheritance](/concepts/composition_vs_inheritance.md) — why Compose favors composition
4. [Recomposition Model](/concepts/recomposition_model.md) — how UI updates without mutation
5. [mutableStateOf](/concepts/mutable_state_of.md) — observable state that triggers recomposition
6. [remember](/concepts/remember.md) — preserving state across recompositions

---

## Declarative UI model

* [Composable Functions](/concepts/composable_functions.md) — `@Composable` functions build UI by calling other composables
* [UI as a Function of State](/concepts/ui_as_function_of_state.md) — render output is derived from current state
* [Composition vs Inheritance](/concepts/composition_vs_inheritance.md) — assemble UI from smaller composables instead of subclassing
* [Recomposition Model](/concepts/recomposition_model.md) — selective re-execution of composables when state changes

---

## State management

* [mutableStateOf](/concepts/mutable_state_of.md) — create observable mutable state
* [State vs MutableState](/concepts/state_vs_mutable_state.md) — read-only vs read-write state interfaces
* [remember](/concepts/remember.md) — cache values across recompositions
* [State Ownership](/concepts/state_ownership.md) — who creates, holds, and mutates state
* [Hoisting State](/concepts/hoisting_state.md) — lift state to the lowest common ancestor
* [Derived State](/concepts/derived_state.md) — compute UI-ready values from other state

---

## Recomposition system

* [Recomposition Triggers](/concepts/recomposition_triggers.md) — what causes Compose to re-run composables
* [Stability](/concepts/stability.md) — when Compose can skip work based on parameter equality
* [Skippable Recompositions](/concepts/skippable_recompositions.md) — how stability enables skipping
* [Keys and Identity](/concepts/keys_and_identity.md) — slot identity for lists and conditional UI
* [Snapshot System](/concepts/snapshot_system.md) — transactional reads and writes of observable state

---

## Layout system

* [Column](/concepts/column.md) — vertical linear layout
* [Row](/concepts/row.md) — horizontal linear layout
* [Box](/concepts/box.md) — stack and overlay children
* [Constraint Layout](/concepts/constraint_layout.md) — constraint-based positioning (conceptual)
* [Modifiers Affecting Layout](/concepts/modifiers_affecting_layout.md) — padding, size, and alignment in the layout pass
* [Intrinsic Measurements](/concepts/intrinsic_measurements.md) — measuring children by content size

---

## Modifiers

* [Modifier Chaining](/concepts/modifier_chaining.md) — functional transformation of composables
* [Ordering Effects](/concepts/ordering_effects.md) — why modifier order matters
* [Layout vs Drawing Modifiers](/concepts/layout_vs_drawing_modifiers.md) — layout, draw, and semantics phases
* [Semantics Modifiers](/concepts/semantics_modifiers.md) — accessibility and testing hooks

---

## Side effects

* [Effect Lifecycle Model](/concepts/effect_lifecycle_model.md) — when effects run relative to composition
* [LaunchedEffect](/concepts/launched_effect.md) — coroutine side effects tied to composition keys
* [SideEffect](/concepts/side_effect.md) — publish Compose state to non-Compose owners
* [DisposableEffect](/concepts/disposable_effect.md) — setup and teardown aligned with lifecycle
* [rememberCoroutineScope](/concepts/remember_coroutine_scope.md) — scope for event-driven coroutines

---

## Lists and performance

* [LazyColumn](/concepts/lazy_column.md) — vertically scrolling lazy lists
* [LazyRow](/concepts/lazy_row.md) — horizontally scrolling lazy lists
* [Item Keys](/concepts/item_keys.md) — stable identity for list items
* [List Diffing](/concepts/list_diffing.md) — how Compose reuses item compositions
* [Performance Pitfalls](/concepts/performance_pitfalls.md) — common recomposition and list mistakes

---

## Animation

* [Animate APIs](/concepts/animate_apis.md) — `animate*` functions for single values
* [Transition APIs](/concepts/transition_apis.md) — animate between discrete UI states
* [State-Driven Animation](/concepts/state_driven_animation.md) — animations as functions of state
* [Spring vs Tween Models](/concepts/spring_vs_tween.md) — physics-based vs timed interpolation

---

## Navigation

* [Navigation Compose](/concepts/navigation_compose.md) — declarative navigation graph
* [Back Stack Model](/concepts/back_stack_model.md) — destinations and back navigation
* [Routes and Arguments](/concepts/routes_and_arguments.md) — typed routes and parameters
* [Lifecycle Interactions](/concepts/lifecycle_interactions.md) — navigation with composition lifecycle

---

## Theming system

* [Composition Locals](/concepts/composition_locals.md) — implicit context propagation
* [Material 3](/concepts/material_3.md) — Material Design theming in Compose
* [Dynamic Color](/concepts/dynamic_color.md) — system-driven color schemes
* [Typography and Shapes](/concepts/typography_and_shapes.md) — text styles and corner radii

---

## Architecture

* [State Hoisting Patterns](/concepts/state_hoisting_patterns.md) — reusable stateful UI patterns
* [Unidirectional Data Flow](/concepts/unidirectional_data_flow.md) — events up, state down
* [MVVM Integration](/concepts/mvvm_integration.md) — ViewModel-driven UI state
* [Repository Integration](/concepts/repository_integration.md) — data layer with Compose UI

---

## Runtime model

* [Compose Compiler Plugin](/concepts/compose_compiler_plugin.md) — compile-time composable transformation (conceptual)
* [UI Tree vs Composition Tree](/concepts/ui_tree_vs_composition_tree.md) — composition, layout, and draw trees

---

## Recommended learning order

### Phase 1 — Core model

1. composable_functions
2. ui_as_function_of_state
3. composition_vs_inheritance
4. recomposition_model
5. mutable_state_of → state_vs_mutable_state → remember
6. state_ownership → hoisting_state → derived_state

### Phase 2 — Recomposition and layout

7. recomposition_triggers → stability → skippable_recompositions
8. keys_and_identity → snapshot_system
9. column → row → box → constraint_layout
10. modifier_chaining → ordering_effects → layout_vs_drawing_modifiers → modifiers_affecting_layout → intrinsic_measurements
11. semantics_modifiers

### Phase 3 — Effects, lists, animation

12. effect_lifecycle_model → launched_effect → side_effect → disposable_effect → remember_coroutine_scope
13. lazy_column → lazy_row → item_keys → list_diffing → performance_pitfalls
14. animate_apis → spring_vs_tween → transition_apis → state_driven_animation

### Phase 4 — Theming, navigation, architecture, runtime

15. composition_locals → material_3 → dynamic_color → typography_and_shapes
16. navigation_compose → back_stack_model → routes_and_arguments → lifecycle_interactions
17. state_hoisting_patterns → unidirectional_data_flow → mvvm_integration → repository_integration
18. compose_compiler_plugin → ui_tree_vs_composition_tree
