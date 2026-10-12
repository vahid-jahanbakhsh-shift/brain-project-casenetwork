# Project brain — CaseNetwork

The **project layer** of a three-layer AI working brain. It says how the work is organised **between**
this project's repositories, and it is loaded into every editor of every member, in every repository
they open. How the code of any one repository is written is not here: that is the repository's own
business, or a **convention set** under `conventions/` that repositories mirror.

The other two layers are the **company** layer (the constraints, and the mechanics of the brain
itself) and each person's own **me** layer. The three never overlap: see § 1 of `CONTRACT.md` in
the company repository.

## Starting this layer

1. Copy this template into a new repository, one per project, named `<family>-project-<project slug>` —
   `brain-project-payments`. The family word is the same for every layer repository here, and
   it is what lets one ruleset protect them all: § 3 bis of `CONTRACT.md`.
2. Pick a short slug for the project and put it in `prefix:` in
   `.github/instructions/00-project-core.instructions.md` — it prefixes this layer's prompts and
   skills, so someone on two projects never gets a collision.
3. Open one of the project's repositories and run `/brain-onboard project`. It fills
   `.github/brain/context.md` from what it can actually read.
4. Write the convention sets under `conventions/` for what several repositories share, and have each
   repository adopt the ones it wants — `/brain-scope-rules`.
5. Set up the governance below.

## Contributing to it

- Anyone drops a **fragment** in `.github/brain/inbox/` — one file, one fact. That is free and
  needs no discussion.
- A maintainer runs `/brain-consolidate project`, which files the fragments into the rules and opens
  a pull request. **That pull request is the project's agreement.**
- What holds for **one repository only** does not belong here: it is a fragment with
  `layer: repository`, filed into that repository's own files by its own consolidation.
- What several repositories share is a **convention set** under `conventions/`, mirrored into each
  adopting repository by a pull request on it. § 1 ter of `CONTRACT.md`.

## Governance

Set the default branch so that **dropping a fragment is free and changing a rule needs
agreement** — a ruleset restricting the consolidated paths, with a bypass for the maintainers.
The exact paths and the fallback are in § 9 of `CONTRACT.md`.
