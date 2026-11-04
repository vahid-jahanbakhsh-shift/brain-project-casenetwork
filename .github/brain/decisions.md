# Decisions

Dated log of choices and **why** they were made. **Most recent first.** The headings are the
index: read them before designing anything structural. A struck-through heading is a decision that
has been replaced — keep it, with a pointer to what replaced it.

Format:

```markdown
## [YYYY-MM-DD] One line stating the decision, not the topic

**What was decided** — in the imperative, precisely enough to be applied.

**Why** — the reasoning, the alternatives considered, and what made them lose. This is the part
that matters in six months.

**What it costs** — the accepted downside. A decision with no downside was not a decision.
```

A decision goes here when it is **settled** and would otherwise be re-litigated: a technology
choice, an architectural boundary, a naming convention, a workflow, a deliberate exception. Not
every choice — only those someone would reasonably reopen.

---

## [2026-10-15] Keep the CaseNetwork project layer synchronized through its own project repository

**What was decided** — Keep the CaseNetwork project layer synchronized through its own project repository.

**Why** — The user chose to sync the project layer; a dedicated remote keeps project context independent from the personal layer and lets it sync across machines and collaborators.

**What it costs** — The project layer requires its own sync and consolidation workflow.

## [2026-10-13] Carry verification data through existing graph responses

**What was decided** — Carry CIMS verified-connection group IDs through the existing case-entity and real-entity link responses, then derive the CaseNetwork verified flag in the frontend instead of adding a separate verification endpoint.

**Why** — The case-entity response already contains these IDs, and adding them to linked-entity responses gives both graph paths the same source-of-truth data while avoiding a separate request.

**What it costs** — Coordinated CIMS and Shift API contract updates, generated-client packaging, and cross-repository tests.

## [2026-10-13] Highlight nodes with any CIMS verified connection

**What was decided** — When CIMS returns at least one verified-connection record for a CaseNetwork node's `realEntityId`, render current-case nodes with a clearer yellow background and expanded verified nodes with a more muted gray-yellow background, even when the linked detection record is not present in the graph.

**Why** — Any verified connection qualifies; current-case verified nodes should be more visually prominent than expanded verified nodes. CIMS is the source of truth for those records.

**What it costs** — Both current-case and expanded graph paths must preserve the same verification predicate while rendering distinct visual emphasis.
