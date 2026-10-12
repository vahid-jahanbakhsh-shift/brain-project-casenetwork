# Context — the ground of this project

**By subject, never by project timeline.** What is durably true about the ground: the stack, the
environments, the controls, the conventions, the measured facts. **Not** a progress journal — that
belongs in the tracker.

Everything below is a **template to fill in**. An empty section is better than a guessed one: the
assistant reads whatever is here as fact.

> **Do not fill this in by hand.** Open a repository of this project and run
> **`/brain-onboard project`**: it reads the project files, the workflows and the branch rules,
> drafts each section from what it actually found, and asks only what it could not read. Run it
> again whenever the ground moves.

> Before writing anything here: no secrets, no credentials, no customer names, no personal data.

## Stack

<!-- Languages, frameworks and versions actually in use. Databases. Runtime and hosting model.
     Anything the assistant would otherwise guess wrong. -->

## Repositories

<!-- The repositories of this project, one line each: what it is, what it is not, and which
     convention sets of `conventions/` it mirrors. **The branch this project builds on in that
     repository**, when it is not the repository's own default — `main` for one project, a client
     fork line such as `clientX` for another. `/brain-workspace new` reads it, and it wins over the
     repository's declaration (§ 1 bis). Where the shared libraries live. Which ones also belong to
     another project — those carry their own conventions, and neither project describes their code.
     This list is what `/brain-check` reads to compare each set against its mirrors, and to find the
     copies of `brain-consolidate/SKILL.md`. -->

## Environments

<!-- Dev, test, staging, production: what exists, who deploys, how a change reaches each one.
     Which environments hold real data — those are never used for experiments. -->

## Workflow and controls

<!-- Branching model. Review policy: how many approvals, who. Required checks. Anything that must
     never be bypassed, and anything needing a formal approval before it can start. -->

## Conventions shared across repositories

<!-- Only what genuinely holds for two or more repositories, and only at the level of the **work**:
     the definition of done, how a change crosses several repositories, the contracts between them.
     Naming, layering, error handling, logging and test layout belong to each repository — written
     there, or in a convention set under `conventions/` that the repository mirrors (§ 1 ter). -->

## Constraints and known facts

<!-- Measured facts that shape decisions: performance ceilings, data volumes, legacy corners
     nobody touches, deprecations with a date, a dependency pinned for a reason. Each with the
     date it was established, so it can be re-checked. -->
