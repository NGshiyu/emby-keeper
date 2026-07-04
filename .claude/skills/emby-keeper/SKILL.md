```markdown
# emby-keeper Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the `emby-keeper` project, a Python backend (Flask) with a modern frontend (Vue.js). You'll learn the project's coding conventions, how to add new API services, and how to extend the frontend with new features or modules. The guide covers file organization, code style, and common development workflows, including suggested commands for frequent tasks.

## Coding Conventions

### File Naming

- **Python files:** Use camelCase (e.g., `userRoutes.py`, `mediaHandler.py`)
- **Frontend files:** Vue components and TypeScript files use PascalCase or camelCase (e.g., `UserPanel.vue`, `mediaUtils.ts`)

### Import Style

- **Python:** Mixed (both absolute and relative imports are used)
    ```python
    # Absolute import
    from embykeeper.api.userRoutes import getUser

    # Relative import
    from .mediaHandler import processMedia
    ```

- **Frontend (TypeScript):** Standard ES6 imports
    ```typescript
    import UserPanel from './components/UserPanel.vue'
    import { useMedia } from './composables/mediaUtils'
    ```

### Export Style

- **Python:** Named exports (functions/classes are explicitly defined and imported)
    ```python
    def getUser(id):
        ...
    ```

- **Frontend (TypeScript):** Named exports for utilities, default exports for components
    ```typescript
    // composables/mediaUtils.ts
    export function useMedia() { ... }

    // components/UserPanel.vue
    export default { ... }
    ```

### Commit Patterns

- **Type:** Freeform (no strict prefixes)
- **Average length:** ~28 characters

## Workflows

### Add New API Service

**Trigger:** When introducing a new backend API service or endpoint group  
**Command:** `/new-api-service`

1. **Create a new API directory or module.**
    - Example: `embykeeper/api/mediaService/`
2. **Add multiple handler files for different endpoints.**
    - Example: `embykeeper/api/mediaService/getMedia.py`
3. **Add an `__init__.py` to the new API module.**
    - This makes the directory a Python package.
4. **Update or create the main entry point to register the new API.**
    - Example: Edit `embykeeper/cli.py` or `embykeeper/app.py` to include:
        ```python
        from embykeeper.api.mediaService import getMedia
        app.register_blueprint(getMedia.bp)
        ```
5. **Optionally add configuration or system files for the API.**

**Example Structure:**
```
embykeeper/
  api/
    mediaService/
      __init__.py
      getMedia.py
      updateMedia.py
  cli.py
```

---

### Add Frontend Feature or Module

**Trigger:** When adding a new feature or section to the frontend web panel  
**Command:** `/new-frontend-feature`

1. **Add new Vue components.**
    - Place in `frontend/src/components/` or `frontend/src/components/ui/`
    - Example: `frontend/src/components/MediaList.vue`
2. **Add new view files.**
    - Place in `frontend/src/views/`
    - Example: `frontend/src/views/MediaView.vue`
3. **Add or update composables.**
    - Place in `frontend/src/composables/`
    - Example: `frontend/src/composables/useMedia.ts`
4. **Update `router.ts` to register new routes if needed.**
    - Example:
        ```typescript
        {
          path: '/media',
          component: () => import('./views/MediaView.vue')
        }
        ```
5. **Update types and utility files.**
    - Example: `frontend/src/types/media.ts`
6. **Update configuration files if needed.**
    - Files: `frontend/package.json`, `frontend/tsconfig.json`, `frontend/vite.config.ts`

**Example Structure:**
```
frontend/
  src/
    components/
      MediaList.vue
    views/
      MediaView.vue
    composables/
      useMedia.ts
    router.ts
    types/
      media.ts
  package.json
  tsconfig.json
  vite.config.ts
```

---

## Testing Patterns

- **Framework:** Unknown (not explicitly detected)
- **File pattern:** Test files are named with `.test.` in the filename (e.g., `apiHandler.test.py`, `useMedia.test.ts`)
- **Location:** Test files are typically placed alongside the code they test or in a dedicated test directory.

**Example (Python):**
```python
# mediaHandler.test.py
from embykeeper.api.mediaHandler import processMedia

def test_process_media():
    ...
```

**Example (Frontend):**
```typescript
// useMedia.test.ts
import { useMedia } from './useMedia'

test('should fetch media', () => {
  ...
})
```

## Commands

| Command               | Purpose                                               |
|-----------------------|-------------------------------------------------------|
| /new-api-service      | Scaffold and register a new backend API service       |
| /new-frontend-feature | Add a new frontend feature or module                  |
```
