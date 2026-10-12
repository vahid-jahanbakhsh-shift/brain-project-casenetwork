---
description: How code is written, designed, tested and shipped on this project. Mirrored into the repositories that adopt it.
applyTo: '**'
---

# Engineering conventions — CaseNetwork

<!-- This is a **convention set**, not a layer file: it is never loaded from here. A repository
     adopts it by copying this file into its own `.github/instructions/`, through a pull request on
     that repository, with `source:` in the copy's frontmatter and the adoption declared in its
     `copilot-instructions.md`. § 1 ter of `CONTRACT.md`.

     Everything below is marked `[initial]`: a starting position carried over from a working brain,
     not something this project has agreed to. Review it, delete what does not fit, date what you
     keep — and delete the whole file rather than shipping a set nobody adopted. -->

## Writing code in an existing codebase

- `[initial]` **Write code that reads like the code around it**: same naming, same idioms, same
  comment density, same error handling, same test style. Read the neighbours before writing.
  Why: a file that reads differently costs every future reader, and gets rewritten by the next
  person who touches it.

- `[initial]` **Follow the existing pattern even when a better one is known.** Raise the better one
  as its own change, never smuggled inside an unrelated fix.
  Why: one change, one decision. A pattern smuggled into a bug fix never gets the discussion it
  needs.

- `[initial]` **Never leave a `TODO`, a commented-out block or a debug trace** in a change that goes
  up for review.
  Why: they survive forever, and they tell the reviewer the change is not finished.

- `[initial]` **Say what a new dependency is and why**, and check what is already in the repository
  first.
  Why: every dependency is a licence question, a security question and a maintenance commitment
  made on someone else's behalf.

## Design

- `[initial]` **No silent fallback.** A partial configuration is an intent, not an absence: fail and
  say what is missing.
  Why: a silent fallback turns a configuration mistake into a behaviour nobody can explain later.

- `[initial]` **When two pieces of work compete for a resource, the lock lives at the level of the
  resource, not of the caller.**
  Why: a lock each caller has to remember to take is a lock that is eventually not taken.

- `[initial]` **A reversible action is offered with its inverse.** No "archive" without "unarchive",
  no "disable" without "enable".
  Why: a one-way gesture traps the user, and the fix always costs more than the inverse would have.

- `[initial]` **In a user interface, when a value belongs to a finite known set, offer the list** —
  multi-select when several values are possible — never a free-text field.
  Why: free text on a known set produces typos that look like data.

## Tests

- `[initial]` **Simple unit tests, no BDD layer** unless this repository already has one and keeps
  it maintained.
  Why: the indirection costs more than it documents, on code that is not a shared specification.

- `[initial]` **Always include the nominal path**: a suite that only exercises refusals sees a
  broken feature as a success.
  Why: a guard that rejects everything, including the valid case, passes a refusal-only suite.

- `[initial]` **Each test sets up and tears down its own world.** Never release a global resource in
  one test's teardown.
  Why: the failure appears in the neighbouring test, and is chased in the wrong file.

- `[initial]` **Exercise the code the way production calls it**, not through a convenient shortcut.
  A user interface is verified by serving the page, not by a green build.
  Why: the shortcut is exactly where the bug is not.

## Documentation

- `[initial]` **The `README.md` orients a developer who has just opened the repository**: a
  "Repository layout" section listing the main folders and files, one line of role each.
  Why: without it, finding where anything lives costs a full read of the tree.

- `[initial]` **Keep the README's layout section current** when a structural folder appears or
  disappears, in the same change.
  Why: documentation updated "later" is documentation that is wrong.

- `[initial]` **A documented command is copyable on its own**: no prompt character, no wrapper, no
  unmarked placeholder.
  Why: every documented command is eventually pasted verbatim by someone in a hurry.

## Git and pull requests

- `[initial]` **Commit path by path** — never `git add -A`, `git add .` or `git commit -a` — after
  reading `git status` and `git diff` on those paths.
  Why: a blanket add sweeps in whatever else is in the tree — a debug edit, a generated file, a
  local config, a secret.

- `[initial]` **A multi-line commit message goes through a file** (`git commit <paths> -F <file>`),
  never a heredoc, never several `-m`.
  Why: a message that goes through a shell loses backticks, accents and backslashes, silently.

- `[initial]` **Push the branch without asking; opening the pull request is a separate gesture**
  made by a person. Prepare the description and show the command.
  Why: the branch notifies nobody. The pull request starts a process, and that is a person's
  signature.

- `[initial]` **A pull request says what changes, why, how it was verified, and what to look at
  first** — and is small enough to review in one sitting.
  Why: the reviewer's time is the scarce resource, and a large pull request is approved, not
  reviewed.

- `[initial]` **Read the existing workflows before proposing a change to CI**, and change the
  smallest thing that works.
  Why: a pipeline is shared. A change that is convenient locally can break everyone's build.

<!-- This file is the **source** of the set, and it lives in the project layer: it changes like any
     other file of that layer — a fragment in its inbox, then `/brain-consolidate project`, then the
     pull request that is the project's agreement. Its **copies**, in the repositories that adopted
     it, carry `source:` and are never edited at all: they follow when this file moves. § 1 ter. -->
