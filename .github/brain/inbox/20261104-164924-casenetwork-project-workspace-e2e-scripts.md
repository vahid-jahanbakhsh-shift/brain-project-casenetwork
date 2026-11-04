---
layer: project
project: casenetwork
type: rule
target: instructions/local-e2e--workspace-specific-scripts.instructions.md
date: 2026-11-04
core: no
author: Copilot
description: 'When creating a CaseNetwork ticket workspace or running E2E: prepare and use workspace-specific start/stop scripts.'
---

# Workspace-specific E2E scripts

- `[2026-11-04]` **Prepare customized `start-e2e-env.ps1` and `revert-e2e-env.ps1` for every CaseNetwork ticket workspace, and use that workspace's scripts when asked to start or stop E2E.**
  Gesture: derive paths from the workspace, select its compatible CIMS checkout and Shift SDK, validate service ownership and startup ordering, and keep configuration edits visible; back up original settings before changing them and restore only captured originals.
  Why: Shared-clone paths and generic process matches can operate on another ticket; preserve Elasticsearch and database data, require approval for resets, and never blindly copy destructive setup or assumed database defaults.

## Story

The supplied local reference pair configures CIMS AppHost, ForceUI E2E settings, a local package feed, and frontend startup. It is not safe to copy unchanged: it hard-codes shared clone paths, hides tracked edits with skip-worktree, automatically installs frontend dependencies, invokes Elasticsearch initialization without checking for destructive setup, matches generic shell commands during shutdown, and restores an assumed local database default rather than its captured original value. Workspace-specific implementations must retain the intended E2E workflow without these hazards.
