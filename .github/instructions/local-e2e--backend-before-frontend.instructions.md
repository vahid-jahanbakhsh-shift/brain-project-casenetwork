---
description: 'When starting CaseNetwork local E2E: wait for the ForceUI backend port before starting the frontend.'
layer: project
test: 'Ask "Start the CaseNetwork local E2E backend and frontend."'
---

- `[2026-10-14]` **Wait until the ForceUI backend port is listening before starting the frontend in a local E2E run.**
  Gesture: check the ForceUI backend listener before launching the frontend.
  Why: The frontend depends on backend routes and ForceUI may take time to initialize its E2E database; starting Vite before the backend is ready creates a misleading partial failure.
