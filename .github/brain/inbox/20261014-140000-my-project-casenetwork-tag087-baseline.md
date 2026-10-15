---
layer: project
type: decision
target: decisions.md
date: 2026-10-14
core: no
---

- [2026-10-14] **Base the FORCE-50113 local CIMS implementation on tag `0.87.0`, apply only the verified-link response change, and use the exact locally generated SDK `0.87.1-force50113.1` in Shift.**
  Why: Current develop introduced unrelated identifier and migration-role contract changes that break Shift's existing DTO mappings. The tag-based feature passes focused CIMS and Shift tests and builds the migration tools without those rewrites. Preserve the develop-based worktree for later merge/release coordination; use `cims-087` as the active local CIMS checkout and do not rerun clean migration without approval.