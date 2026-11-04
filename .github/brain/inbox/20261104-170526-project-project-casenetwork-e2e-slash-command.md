---
layer: project
project: casenetwork
type: decision
target: decisions.md
date: 2026-11-04
core: no
author: Copilot
---

# Propose a CaseNetwork E2E slash command

- `[2026-11-04]` **Provide a project-prefixed slash command for starting the current CaseNetwork ticket workspace's E2E environment through its workspace-specific scripts.**
  Gesture: prepare a discoverable project prompt or skill that resolves the current ticket workspace, checks prerequisites and service ownership, uses its customized startup script, preserves existing data, and requests approval before initialization or resets.
  Why: A short command makes the established cross-repository E2E procedure easy to invoke without repeating the startup instructions.

## Story

The user requested a slash command after receiving a natural-language startup example. Proposed interface: `/casenetwork-e2e start`, with an optional `stop` action using the workspace's revert script. The exact interface and optional stop action remain proposals, not adopted project guidance. Implement through project promotion and consolidation review; do not start services merely by capturing this proposal.
