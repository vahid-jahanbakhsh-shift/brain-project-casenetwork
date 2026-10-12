# Inbox — captures waiting to be filed

One file per fact. Written during the work, filed later by `/brain-consolidate`.

Name: `YYYYMMDD-HHMMSS-<recipient>-<layer>[-<project>]-<slug>.md` — the destination, owning layer,
and project when applicable are visible without opening the fragment.

```markdown
---
layer: me | project | company | repository
repository: <name>                # only when layer is repository
type: rule | decision | lesson | context | reference
target: rules/<subject>.md        # repository: copilot-instructions.md, or instructions/<x>.instructions.md
date: YYYY-MM-DD
core: yes | no
---

<the body, already in the format of the target file>
```

The full definition, and the consolidation rules, are in § 7 and § 8 of the contract.

**Never file a capture by editing a rules file mid-task.** One file here costs seconds and never
conflicts; an edit to a shared file costs a merge, and the capture that costs a merge is the
capture that gets dropped.
