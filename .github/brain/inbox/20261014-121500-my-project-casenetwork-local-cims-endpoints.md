---
layer: project
type: context
target: context.md
date: 2026-10-14
core: no
---

- [2026-10-14] **For the CaseNetwork local E2E workspace, configure Shift's CaseManagementService URL to the CIMS Aspire proxy at `https://localhost:7279`; `https://localhost:17275` is the Aspire dashboard.**
  Why: Probing `/livez` and `/readyz` on port 7279 returned HTTP 200 through the CIMS proxy, while 17275 served the AppHost dashboard. Using the dashboard port in ForceUI configuration causes CIMS requests to fail.