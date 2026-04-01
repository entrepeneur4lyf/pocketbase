```markdown
# pocketbase Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill provides a comprehensive guide to the development practices and workflows used in the `pocketbase` repository, a Go-based project. It covers coding conventions, file organization, and step-by-step instructions for common maintenance and release workflows. Whether you are contributing code, updating dependencies, or managing releases, this guide will help you follow the established patterns of the codebase.

## Coding Conventions

### File Naming

- **Style:** `snake_case`
- **Example:**  
  - `user_service.go`
  - `modernc_versions_check.go`

### Imports

- **Style:** Use import aliases where appropriate.
- **Example:**
  ```go
  import (
      pb "github.com/pocketbase/pocketbase"
      "fmt"
  )
  ```

### Exports

- **Style:** Mixed (both exported and unexported symbols are used as needed).
- **Example:**
  ```go
  // Exported
  func PublicFunction() {}

  // Unexported
  func privateFunction() {}
  ```

### Commit Messages

- **Style:** Freeform, no strict type or prefix required.
- **Average Length:** ~38 characters

## Workflows

### Update UI Dist and Env
**Trigger:** When updating built frontend assets or after making frontend changes/updating npm dependencies.  
**Command:** `/update-ui-dist`

1. Update `ui/.env` if needed.
2. Build the frontend (generates new files in `ui/dist/assets/` and `ui/dist/index.html`).
3. Update `ui/package-lock.json` if npm dependencies changed.
4. Update `CHANGELOG.md` if relevant.

**Example:**
```sh
# Update environment variables
vim ui/.env

# Build frontend (example command)
cd ui && npm run build

# Update changelog
vim CHANGELOG.md
```

---

### Bump Go Dependencies
**Trigger:** When updating Go dependencies or upgrading a Go library.  
**Command:** `/bump-go-deps`

1. Update `go.mod` and `go.sum`.
2. Update related version check files (e.g., `modernc_versions_check.go`).
3. Update `CHANGELOG.md` if relevant.

**Example:**
```sh
go get -u some/dependency
go mod tidy
vim modernc_versions_check.go
vim CHANGELOG.md
```

---

### Regenerate JSVM Types
**Trigger:** When Go types or APIs related to JSVM change and TypeScript definitions need to be synced.  
**Command:** `/regenerate-jsvm-types`

1. Regenerate `plugins/jsvm/internal/types/generated/types.d.ts`.
2. Optionally update `plugins/jsvm/internal/types/types.go`.
3. Optionally update `CHANGELOG.md`.

**Example:**
```sh
# Regenerate TypeScript types (example script)
go run plugins/jsvm/internal/types/cmd/gen_types.go

# Optionally update Go types and changelog
vim plugins/jsvm/internal/types/types.go
vim CHANGELOG.md
```

---

### Bump App Version
**Trigger:** When releasing a new version or incrementing the app version.  
**Command:** `/bump-version`

1. Update `ui/.env` with the new version.
2. Regenerate `ui/dist/assets/*` and `ui/dist/index.html`.
3. Update `CHANGELOG.md`.
4. Optionally update `README.md`, `CONTRIBUTING.md`, `.github/workflows/release.yaml`.

**Example:**
```sh
vim ui/.env
cd ui && npm run build
vim CHANGELOG.md
vim README.md
vim CONTRIBUTING.md
vim .github/workflows/release.yaml
```

---

### Fix or Update Changelog
**Trigger:** When recording changes, fixes, or backports in the changelog.  
**Command:** `/update-changelog`

1. Edit `CHANGELOG.md` or `CHANGELOG_*.md`.
2. Commit the changelog update.

**Example:**
```sh
vim CHANGELOG.md
git add CHANGELOG.md
git commit -m "Update changelog for recent changes"
```

## Testing Patterns

- **Framework:** Unknown (no Go-specific test framework detected).
- **File Pattern:** For TypeScript, tests are in files matching `*.test.ts`.
- **Example:**
  ```typescript
  // user_service.test.ts
  import { describe, it, expect } from 'some-test-lib';

  describe('UserService', () => {
    it('should create a user', () => {
      // test logic
    });
  });
  ```

## Commands

| Command               | Purpose                                                         |
|-----------------------|-----------------------------------------------------------------|
| /update-ui-dist       | Update frontend build output and environment configuration      |
| /bump-go-deps         | Update Go module dependencies                                  |
| /regenerate-jsvm-types| Regenerate TypeScript types for JSVM plugins                   |
| /bump-version         | Bump the app version and regenerate UI assets                  |
| /update-changelog     | Update or fix the changelog files                              |
```