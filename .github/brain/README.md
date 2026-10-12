# The project layer — map

The knowledge layer of this project's brain: the work between its repositories. It is **not** loaded
on every exchange — the always-on part is `../instructions/00-project-core.instructions.md`, and it is
deliberately short.

**This map is authoritative.** Any file created, merged or moved is reflected here in the same
move: an index that lies is worse than no index.

<!-- `rules/` and `lessons/` start empty on purpose. Add one line per file as you create it, and
     replace the `<subject>` rows below once you have real subjects. -->

| File | Contents | When to write to it |
|---|---|---|
| [context.md](context.md) | The ground: stack, repositories, environments, controls, conventions, measured facts | Filled by `/brain-onboard project`; re-run it when the ground moves |
| `rules/<subject>.md` | The full text of the rules on one subject — architecture, environments, procedures | A choice that holds between repositories is settled |
| [decisions.md](decisions.md) | Dated log of settled choices and **why**, most recent first | A choice is settled (technology, architecture, boundary) |
| [lessons/](lessons/) | Principles paid for by a real failure, one file per subject | An experience yields something that must not be relearnt |
| [inbox/](inbox/README.md) | Fragments waiting to be filed | `/brain-promote` writes here; `/brain-consolidate project` empties it |

Per-language and per-folder code rules are **not** here and not in `../instructions/` either: they
live in the repositories (§ 1 bis of `CONTRACT.md`), written there or mirrored from a **convention
set** under `../../conventions/` (§ 1 ter). Write them with `/brain-scope-rules`.

## How to read it

1. `../instructions/00-project-core.instructions.md` is always in context, together with the company
   and personal cores.
2. Read the `rules/<subject>.md` that matches the work at hand, before acting.
3. Read the headings of `decisions.md` as soon as the work touches architecture, security, data or
   naming.
4. Read `lessons/<subject>.md` when approaching a problem of a kind that has already bitten.

## How to write to it

**Never by editing these files in the middle of a task.** A capture goes to the personal inbox with
`layer: project`; `/brain-promote` pushes it into `inbox/` here; `/brain-consolidate project` files it and
opens a pull request — **that pull request is the project's agreement**.

What concerns **one repository only** does not belong here: it is a fragment with
`layer: repository`, filed into that repository's own files by its own consolidation.

The formats — a rule, a lesson, a fragment — are in `CONTRACT.md` in the company layer, § 6 to § 7.
