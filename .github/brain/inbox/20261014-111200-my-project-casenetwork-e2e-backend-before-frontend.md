---
layer: project
type: rule
target: rules/local-e2e.md
date: 2026-10-14
core: no
---

- [2026-10-14] **Wait until the ForceUI backend port is listening before starting the frontend in a local E2E run.**
  Why: The frontend depends on backend routes and ForceUI may take time to initialize its E2E database; starting Vite before the backend is ready creates a misleading partial failure.