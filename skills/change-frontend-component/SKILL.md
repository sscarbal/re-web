---
name: change-frontend-component
description: Create or refactor Re_ Astro/React frontend components with minimal JavaScript and protected locale, accessibility, content, and performance contracts. Use for component extraction, reuse, API changes, styling refactors, or template decoupling.
---

# Change a frontend component

## Inputs

- Requested behavior, current component, callers, content schema and acceptance criteria.
- Required breakpoints/locales and approved design reference.

## Procedure

1. Inspect all usages, props, rendered HTML, styles, hydration directive and shared-package behavior.
2. Define behavior to preserve and defect/debt to remove.
3. Prefer an Astro component; retain React only for necessary client state.
4. Make the smallest coherent API change and update all callers atomically.
5. Preserve locale-aware URLs, semantic roles, keyboard/focus behavior, alt/labels and reduced motion.
6. Add or update tests for rendering, helpers and critical interactions.
7. Run check, lint, build, link/asset and browser tests relevant to the component.

## Quality checklist

- No nested interactive elements, pseudo-links or client-only essential content.
- Props are typed and invalid content fails early.
- JS and dependency cost does not increase without evidence.
- ES/EN and mobile/desktop behavior are verified.

## Expected output

A focused component diff, updated callers/tests, validation results, visual evidence and migration notes if the API changed.

## Avoid

- Refactoring unrelated code.
- Copying opaque upstream components without auditing markup.
- Adding abstractions with only one speculative consumer.

