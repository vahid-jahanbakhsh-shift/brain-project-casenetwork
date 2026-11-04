# The project layer — map

The knowledge layer of this project's brain: the work between its repositories. It is **not** loaded
on every exchange — the always-on part is `../instructions/00-project-core.instructions.md`, and it is
deliberately short.

**This map is authoritative.** Any file created, merged or moved is reflected here in the same
move: an index that lies is worse than no index.

| File | Contents | When to write to it |
|---|---|---|
| [context.md](context.md) | The ground: stack, repositories, environments, controls, conventions, measured facts | Filled by `/brain-onboard project`; re-run it when the ground moves |
| [../instructions/git-and-github--lowercase-hyphenated-branches.instructions.md](../instructions/git-and-github--lowercase-hyphenated-branches.instructions.md) | CaseNetwork branch naming | A project-wide branch naming convention changes |
| [../instructions/local-e2e--backend-before-frontend.instructions.md](../instructions/local-e2e--backend-before-frontend.instructions.md) | Local E2E startup ordering | Backend and frontend startup dependencies change |
| [../instructions/local-e2e--workspace-specific-scripts.instructions.md](../instructions/local-e2e--workspace-specific-scripts.instructions.md) | Workspace-specific E2E start/revert scripts and safe configuration restoration | Creating a ticket workspace or starting/stopping its E2E environment |
| [../prompts/casenetwork-e2e.prompt.md](../prompts/casenetwork-e2e.prompt.md) | `/casenetwork-e2e start|stop` workflow for the current ticket workspace | Starting or stopping ticket-local E2E |
| [../instructions/cross-repo--cims-sdk-compatibility.instructions.md](../instructions/cross-repo--cims-sdk-compatibility.instructions.md) | Generated-client schema and runtime compatibility between CIMS and Shift | SDK integration validation changes |
| [decisions.md](decisions.md) | Dated log of settled choices and **why**, most recent first | A choice is settled (technology, architecture, boundary) |
| [inbox/](inbox/README.md) | Fragments waiting to be filed | `/brain-promote` writes here; `/brain-consolidate project` empties it |

Per-language and per-folder code rules are **not** here and not in `../instructions/` either: they
live in the repositories (§ 1 bis of `CONTRACT.md`), written there or mirrored from a **convention
set** under `../../conventions/` (§ 1 ter). Write them with `/brain-scope-rules`.

## How to read it

1. `../instructions/00-project-core.instructions.md` is always in context, together with the company
   and personal cores.
2. Read the matching card in `../instructions/` before naming branches, creating a ticket workspace, or consuming a generated CIMS SDK; use `/casenetwork-e2e start|stop` for ticket-local E2E.
3. Read the headings of `decisions.md` as soon as the work touches architecture, security, data or
   naming.
4. Lessons that produce a rule live in its card; historical incident detail is preserved in the consolidation commit.

## How to write to it

**Never by editing these files in the middle of a task.** A capture goes to the personal inbox with
`layer: project`; `/brain-promote` pushes it into `inbox/` here; `/brain-consolidate project` files it and
opens a pull request — **that pull request is the project's agreement**.

What concerns **one repository only** does not belong here: it is a fragment with
`layer: repository`, filed into that repository's own files by its own consolidation.

The formats — a rule, a lesson, a fragment — are in `CONTRACT.md` in the company layer, § 6 to § 7.
