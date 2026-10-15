---
layer: project
type: decision
target: decisions.md
date: 2026-10-13
core: no
---

- [2026-10-13] **Carry CIMS verified-connection group IDs through the existing case-entity and real-entity link responses, then derive the CaseNetwork verified flag in the frontend instead of adding a separate verification endpoint.**
  Why: The case-entity response already contains these IDs, and adding them to linked-entity responses gives both graph paths the same source-of-truth data while avoiding a separate request. The cost is coordinated CIMS and Shift API contract updates, generated-client packaging, and cross-repository tests.