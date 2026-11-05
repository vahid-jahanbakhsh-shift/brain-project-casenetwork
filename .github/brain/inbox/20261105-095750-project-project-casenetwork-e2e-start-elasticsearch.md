---
layer: project
project: casenetwork
type: decision
target: decisions.md
date: 2026-11-05
core: no
author: Copilot
---

# Start Elasticsearch with CaseNetwork ticket E2E

- `[2026-11-05]` **Make CaseNetwork ticket E2E startup start Elasticsearch when no healthy local instance is available, wait until it is healthy, and never reset or reinitialize existing Elasticsearch data.**
  Gesture: have `/casenetwork-e2e start` and each ticket workspace's startup script start or reuse healthy Elasticsearch before CIMS and ForceUI; preserve existing data and track only processes started by that workspace.
  Why: The current script only probes port 9209 and aborts if Elasticsearch is unavailable, so it does not bring up the complete E2E environment.

## Story

The user clarified that the CaseNetwork E2E slash command should start Elasticsearch too. Whether the `stop` action should stop an Elasticsearch process started by that workspace remains unspecified; do not infer that behavior from this capture.
