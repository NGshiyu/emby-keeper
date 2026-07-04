---
name: add-new-api-service
description: Workflow command scaffold for add-new-api-service in emby-keeper.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /add-new-api-service

Use this workflow when working on **add-new-api-service** in `emby-keeper`.

## Goal

Adds a new backend API service, including multiple route handler files and initialization.

## Common Files

- `embykeeper/api/__init__.py`
- `embykeeper/api/*.py`
- `embykeeper/cli.py`
- `embykeeperapi/__init__.py`
- `embykeeperapi/*.py`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create a new API directory or module.
- Add multiple handler files for different API endpoints.
- Add an __init__.py to the new API module.
- Update or create a main entry point (e.g., cli.py or app.py) to register the new API.
- Optionally add configuration or system files for the API.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.