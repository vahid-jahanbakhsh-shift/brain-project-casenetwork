---
layer: project
type: lesson
target: lessons/cross-repo-sdk-compatibility.md
date: 2026-10-13
core: no
---

- [2026-10-13] **Before consuming a locally generated CIMS client in Shift, verify the package's full generated schema against Shift's current package baseline, not only the endpoint being changed.**
  Why: The local CIMS client included unrelated attribute DTO changes (`Identifier` objects and removal of `DriverLicenseNumbers`) that made Shift fail to compile despite the CaseNetwork response change being additive. Ignoring this mismatch either blocks validation or expands a focused ticket into unrelated data-mapping changes.
  Verified on 2026-10-14: The ForceUI migration tools load SDK `0.87.0`, which models bulk case-entity roles as `BulkCaseEntityRoleData` objects (`Role`, `SourceRole`), while the current CIMS API expects strings. Migration logs show HTTP 400 at `$.data.caseEntityRecords[2].roles[0]`; an earlier failure concerned `attributes.business.identificationNumbers[0]`. A successful Shift build with the old SDK does not establish wire compatibility with the current CIMS API.