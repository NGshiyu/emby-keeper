---
name: add-frontend-feature-or-module
description: Workflow command scaffold for add-frontend-feature-or-module in emby-keeper.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-frontend-feature-or-module

Use this workflow when working on **add-frontend-feature-or-module** in `emby-keeper`.

## Goal

Adds a new frontend feature or module, typically including new components, views, composables, and updates to configuration and type files.

## Common Files

- `frontend/src/components/*.vue`
- `frontend/src/components/ui/*.vue`
- `frontend/src/views/*.vue`
- `frontend/src/composables/*.ts`
- `frontend/src/router.ts`
- `frontend/src/types/*.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Add new Vue components (in src/components or src/components/ui).
- Add new view files (in src/views).
- Add or update composables (in src/composables).
- Update router.ts to register new routes if needed.
- Update types and utility files.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.