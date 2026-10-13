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

- `app-case-intel-management-service` (CIMS): C# 13, .NET 10 / ASP.NET Core, Azure SQL, and .NET Aspire for local orchestration. It includes a typed .NET client and API, migration, extraction, and IntelSearch projects.
- `shift`: a large multi-product monorepo containing Force UI and Shift client solutions. Select the owning solution and its repository guidance for each ticket; the repository root is not one single application.
- `i18n-cdn-assets`: translation source management and a TypeScript package. It uses Yarn 4.17.1 and its documented local setup is a Node 22 Dev Container.

## Repositories

- `app-case-intel-management-service` (`shift-technology/app-case-intel-management-service`) — CIMS case-management API and supporting services; start branches from `origin/develop`.
- `shift` (`shift-technology/shift`) — broad Shift monorepo, including Force UI and client solutions; start branches from `origin/develop`. For Force UI frontend changes, follow the repository's `force-ui-frontend-expert` skill.
- `i18n-cdn-assets` (`shift-technology/i18n-cdn-assets`) — translation sources and the i18n TypeScript package; start branches from `origin/main`. Use its Dev Container for local editing and PR work; do not require sibling repositories to be available inside that container.

## Environments

- CIMS has pre-production deployment-test workflows. i18n publishes locale assets to its production environment from `main` and staging from `beta`.
- Which environments contain real data and who owns or approves deployments for CIMS, Shift, and i18n have not been confirmed. Do not infer data classification or deployment authority from workflow names.

## Workflow and controls

- Create a separate pull request for each repository changed by a ticket. Keep changes within the repositories explicitly in that ticket's scope; do not make opportunistic changes in other project repositories.
- Obtain formal approval before adding a dependency, changing a database/schema, or changing an API contract.
- `shift` and CIMS require code-owner review and approval of the last push. Shift's `develop` ruleset requires the generated DMV2 contract check. Owners and any further checks depend on the affected paths.
- i18n requires at least one approval, code-owner review, and its `validation` check; only squash merging is allowed. `platform-ui` owns all PRs; FORCE locale changes also require `ds-datamodel-owners`, and language-owner rules can apply by path.

## Conventions shared across repositories

No shared code-style convention has been confirmed. Follow each repository's own instructions, skills, and checks; use separate pull requests for each changed repository.

## Constraints and known facts

No known legacy areas or other constraints to avoid have been identified.
