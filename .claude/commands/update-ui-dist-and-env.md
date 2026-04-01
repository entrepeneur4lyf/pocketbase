---
name: update-ui-dist-and-env
description: Workflow command scaffold for update-ui-dist-and-env in pocketbase.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /update-ui-dist-and-env

Use this workflow when working on **update-ui-dist-and-env** in `pocketbase`.

## Goal

Updates the UI build output and environment configuration, often after frontend changes or dependency updates.

## Common Files

- `ui/.env`
- `ui/dist/assets/*.js`
- `ui/dist/index.html`
- `ui/package-lock.json`
- `CHANGELOG.md`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update ui/.env if needed
- Build the frontend (generates new files in ui/dist/assets/ and ui/dist/index.html)
- Update ui/package-lock.json if npm deps changed
- Update CHANGELOG.md if relevant

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.