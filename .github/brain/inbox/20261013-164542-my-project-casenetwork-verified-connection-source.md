---
layer: project
type: context
target: context.md
date: 2026-10-13
core: no
---

- [2026-10-13] **Use CIMS `GET /real-entities/{realEntityId}/verified-connections` as the source of truth for CaseNetwork node verification; Shift already reads these records for transaction matches, but its graph-facing entity and link responses do not expose a verified marker.**
  Why: Inspection of the CIMS controller, Shift `TransactionMatchService`, graph API consumers, and graph response view models confirmed this existing data path and the missing graph-facing status.
