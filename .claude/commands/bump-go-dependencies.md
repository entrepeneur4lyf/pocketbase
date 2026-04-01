---
name: bump-go-dependencies
description: Workflow command scaffold for bump-go-dependencies in pocketbase.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /bump-go-dependencies

Use this workflow when working on **bump-go-dependencies** in `pocketbase`.

## Goal

Updates Go module dependencies, including go.mod and go.sum, sometimes with related version check files.

## Common Files

- `go.mod`
- `go.sum`
- `modernc_versions_check.go`
- `CHANGELOG.md`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update go.mod and go.sum
- Update related version check files (e.g., modernc_versions_check.go)
- Update CHANGELOG.md if relevant

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.