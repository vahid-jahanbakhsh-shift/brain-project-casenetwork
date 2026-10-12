---
name: brain-consolidate
description: File the fragments waiting in an inbox into that level's rules, decisions and lessons, then check the structure still holds. Takes a level - me, project, repository or company. Use when someone asks to consolidate the brain or empty its inbox, when a piece of work ends, when an inbox holds more than about ten fragments, and when a scheduled job hands a repository to a coding agent for its nightly consolidation.
---

# Consolidate

Empty one level's inbox into that level's own files, then verify the structure still fits what it
holds. **One level per run**: `me`, `project`, `repository` or `company`.

## Where the inbox is

- `me` — `<ME>/.github/brain/inbox/`, from the manifest in the personal core.
- `project` / `company` — `.github/brain/inbox/` of that layer's repository. When this skill runs
  inside that repository (a maintainer working there, or a coding agent given an issue), the inbox
  is simply `.github/brain/inbox/` of the current workspace.
- `repository` — `.github/brain/inbox/` of the **code** repository being consolidated. Its files are
  `.github/copilot-instructions.md` and `.github/instructions/*.instructions.md`; it has no layer of
  its own (§ 1 bis of the contract).

If the current workspace is not the level being consolidated and its root is not in the manifest,
say so and stop rather than guessing a path.

## Before anything

**Bring the level up to date** — `git -C <root> fetch origin --prune`, then `pull --ff-only`; or
`/brain-sync`, when slash commands are available here. Filing on a stale clone files a rule beside
the one that already replaced it upstream, and the contradiction surfaces in the pull request
instead of in this pass.

**Uncommitted fragments in the inbox are the normal state here** — they are exactly what this pass
is about to file, and they do not block a fast-forward. Stop only if the fast-forward itself is
refused, or if a **tracked** file of the level has local edits: both mean a person has to look, and
neither is something this procedure should resolve.

**`repository` only — one consolidation at a time.** If a consolidation pull request is still open
on this repository, **stop and say so**. Two of them edit the same instruction files and conflict,
which is exactly what the inbox exists to prevent; starting a second one gives the conflict back.

## Steps

1. **List** every file in the inbox, excluding `README.md`. If it is empty, say so and stop.
2. **Read them all before writing anything.** Two fragments often say the same thing from two
   angles, or one corrects another: merge them into a single rule rather than filing both.
3. **Set aside every fragment whose `layer:` is not the level being consolidated** — and, on a
   repository, every fragment whose `repository:` names another one. They are never filed here. List
   them at the end as waiting for `/brain-promote`, and leave them in place.
4. For each remaining fragment, in order:
   - Open its `target` file inside this level. **Look for a rule that already covers it.** If one
     exists, *update* it: a rule that became false is corrected or deleted, never stacked next to
     its replacement.
   - Otherwise add it in the right section, in that file's own format: `[YYYY-MM-DD]` — the date it
     is filed, never `[initial]`, which marks only what a level shipped with — imperative, one
     line, followed by its `Why:`.
   - If `core: yes` **and** the three conditions genuinely hold (fires every exchange, fails
     silently, no tool enforces it), add **one line** to this level's always-loaded file as well —
     a layer's core, a repository's `copilot-instructions.md` — with the full text in its `rules/`
     file or its scoped file. If it would pass **100 lines**, do not raise the ceiling: move an
     existing rule down, or compact at constant meaning.
   - **Never touch a file carrying `source:` in its frontmatter.** It is a mirror of a convention
     set (§ 1 ter): it changes only through the pull request that updates the set. A fragment that
     contradicts one is filed in the repository's **own** files, and the contradiction is reported,
     so that the set is updated or the adoption dropped.
   - **Delete the fragment file, in the same commit as the filing.** A fragment that survives its
     own consolidation gets filed twice.
5. **Check the structure**, and fix it in the same pass:
   - A file mixing two unrelated subjects → split it.
   - The same fact in two places → one source, the other becomes a pointer.
   - Content that belongs to another level → do not file it; list it for promotion.
   - A file that journals what lives in the tracker → strip the duplication out.
   - New content that fits nowhere → create the file, do not force it.
   - Update the map in `.github/brain/README.md` for anything created, merged or moved.
6. **Propose the movements between levels**, without applying them unasked:
   - `repository` — a rule here that has now been seen in **two or more** repositories → propose
     lifting it into a **convention set** of the project layer, which this repository then mirrors;
   - `project` — a rule here that turns out to describe **one** repository, or how a repository's
     code is written at all → propose moving it **down**: into that repository, or into a
     convention set;
   - either — a per-language or per-folder code rule sitting under a layer's `.github/instructions/`
     is in the wrong place by construction (§ 5 bis). Say so.
7. **Commit**, path by path, with a message listing what was consolidated. Then:
   - `me` — straight on the default branch. No approval, no ceremony.
   - `project` — on a branch `brain/consolidate-YYYYMMDD`, then a pull request. **Ask before opening
     it**: it is visible to everyone on the project. That pull request is the project's agreement.
   - `repository` — the same, on a branch of that repository, reviewed like any other change to it,
     and **one at a time**.
   - `company` — same, and it needs the committee's approvals.
8. **Report**: how many fragments were filed and into which files, what was merged or corrected,
   what changed in the structure, and what is waiting for promotion.

## Rules

- **Move content without rewriting it.** Compacting a wording is allowed; changing what it says is
  not. A consolidation is a filing pass, not an editing pass.
- **Ask before deleting anything that is not a fragment file.**
- **Never let an always-loaded file pass its ceiling**, and never create a second "loaded by
  situation" core — that layer already exists as `rules/` and as scoped instruction files.
- A fragment is filed **or** listed for promotion. Never both, never neither.
