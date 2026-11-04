---
description: 'Before consuming a locally generated CIMS SDK in Shift: check the full schema and runtime wire compatibility.'
layer: project
test: 'Ask "Consume a locally generated CIMS client in Shift for an additive response change."'
---

- `[2026-10-14]` **Before consuming a locally generated CIMS client in Shift, verify the full generated schema against Shift's package baseline and its runtime wire compatibility with the target CIMS API.**
  Gesture: check all generated DTO changes, compile affected Shift consumers, and validate migration request payloads against the target API; a build alone is insufficient.
  Why: Unrelated identifier DTO changes broke compilation, while bulk role objects sent to an API expecting strings caused HTTP 400 despite a successful build.
