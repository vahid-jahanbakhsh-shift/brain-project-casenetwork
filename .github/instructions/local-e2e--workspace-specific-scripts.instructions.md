---
description: 'When creating a CaseNetwork ticket workspace or running E2E: prepare and use workspace-specific start/stop scripts.'
layer: project
test: 'Ask "Create a CaseNetwork ticket workspace, then start and stop its E2E environment."'
---

- `[2026-11-04]` **Prepare customized `start-e2e-env.ps1` and `revert-e2e-env.ps1` for every CaseNetwork ticket workspace, and use that workspace's scripts when asked to start or stop E2E.**
  Gesture: derive paths from the workspace, select its compatible CIMS checkout and Shift SDK, validate service ownership and startup ordering, and keep configuration edits visible; back up original settings before changing them and restore only captured originals.
  Why: Shared-clone paths and generic process matches can operate on another ticket; preserve Elasticsearch and database data, require approval for resets, and never blindly copy destructive setup or assumed database defaults.
