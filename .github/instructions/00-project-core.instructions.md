---
description: The work between this project's repositories. Loaded on every exchange.
applyTo: '**'
contract: 1
layer: project
prefix: casenetwork
fresh-until: 2026-11-12
---

# Project core — CaseNetwork

<!-- `casenetwork` prefixes this layer's prompts and skills. Refresh `fresh-until:` when the project
     context is reviewed or merged, using roughly one month after that date. -->

## What this layer holds

The **work between this project's repositories**: the ground, the map of the repositories and what
each is for, the environments, cross-repository architecture decisions, lessons, procedures, the
definition of done. Not the company's constraints (they are in the company layer), not one person's
preferences (those are in theirs), and **never how a repository's code is written** — that lives in
the repository itself, or in a convention set under `conventions/` that repositories mirror (§ 1 bis
and § 1 ter of `CONTRACT.md`).

## Precedence

**Precedence.** A constraint beats a convention; a convention beats a preference — company, then
project, then me. A lower layer may be stricter than a higher one, never looser. On a repository's
code, that repository's own instruction files win over any project layer: the closest description
of the code is the truest. When two loaded layers genuinely conflict, follow the higher one, say
so in one line, and capture the conflict.

## Where to write

Captures go to the **personal** inbox, like every other capture; `/brain-promote` moves the ones
marked `layer: project` into `.github/brain/inbox/` of this repository. They are filed from there by
`/brain-consolidate project`, which opens a pull request — **that pull request is the project's
agreement**.

This layer is a clone and nothing updates it: past the `fresh-until` date in the frontmatter above
— or with no date set — say it once at the start of the session, and offer `/brain-sync`. Past it,
a convention read here was never this project's agreement.

## The rules

<!-- One line per rule, imperative. The full text of each subject lives in
     `.github/brain/rules/<subject>.md`. A rule belongs here only if it fires on something every
     exchange does, and getting it wrong fails silently. Hard ceiling: 100 lines for this file. -->

- `[2026-09-29]` **If this project's prefix is present in the personal manifest but absent from the company registry, continue project work and point to `/brain-project register`; stop and report if `brain-me`, `brain-company`, or this project root is missing from the manifest.**

## Conventions shared by several repositories

<!-- One line per set in `conventions/`. A set is the source; a repository adopts it by mirroring it
     into its own `.github/instructions/`, through a pull request on that repository. Never edit a
     mirrored copy, and never write a per-language rule into this layer's `.github/instructions/`.
     `templates/project/conventions/engineering.instructions.md` is the default set shipped here:
     keep it, adapt it, or delete it. -->

- <!-- e.g. `[initial]` **`conventions/engineering.instructions.md`** — writing code, design, tests, git. -->

## Read on demand

| Subject | File |
|---|---|
| The ground: stack, repositories, environments, controls, conventions | `.github/brain/context.md` |
| Settled choices and why | `.github/brain/decisions.md` |
| Rules, by subject | `.github/brain/rules/<subject>.md` |
| Conventions repositories mirror | `conventions/<subject>.instructions.md` |
| Principles paid for by a real failure | `.github/brain/lessons/<subject>.md` |

If `.github/brain/context.md` is still empty, say so **once** at the start of the session and
offer `/brain-onboard project`. Without it, every answer is generic advice about an imaginary
project. Do not repeat the offer in the same session.
