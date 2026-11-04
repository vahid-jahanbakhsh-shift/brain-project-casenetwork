---
name: casenetwork-e2e
description: 'Start or stop local E2E for the current CaseNetwork ticket workspace using its workspace-specific scripts.'
argument-hint: start | stop
agent: agent
---

# CaseNetwork ticket E2E

Run this prompt as `/casenetwork-e2e start` or `/casenetwork-e2e stop`. The argument must be `start` or `stop`. If it is missing or invalid, ask the user which action they want; do not assume `start`.

## Resolve the current ticket workspace

1. Identify the open ticket workspace's `workspace-notes` folder and the sibling repository roots `shift`, `app-case-intel-management-service`, and `i18n-cdn-assets`.
2. Resolve their common parent. Continue only when all four folders are direct children of that same parent and both `start-e2e-env.ps1` and `revert-e2e-env.ps1` exist there.
3. If the current workspace or script location is ambiguous, ask the user to open or identify the ticket workspace; do not search outside the open workspace or use a remembered path.
4. Read the CaseNetwork `local-e2e--workspace-specific-scripts` and `local-e2e--backend-before-frontend` instruction cards. If the task involves a locally generated CIMS SDK, also follow `cross-repo--cims-sdk-compatibility`.
5. Use PowerShell 7 (`pwsh`), never Windows PowerShell 5.1, and quote the resolved absolute script path.

## `start`

1. The script checks required files, existing Elasticsearch health on port 9209, ports it needs, frontend dependencies, and the ForceUI migration tool.
2. Before starting services, explain that CIMS runs schema migrations and may run a `--clean` data migration, and ForceUI initializes its E2E database. Ask the user for explicit approval for these local data operations. The `/casenetwork-e2e start` request alone is not that approval.
3. If approval is declined, do not invoke the start script.
4. After approval, run:

   ```powershell
   pwsh -NoProfile -File '<ticket-workspace>\start-e2e-env.ps1' -ApproveLocalDataInitialization
   ```

5. Report the script's result and any errors exactly. It starts CIMS before ForceUI and the frontend, reuses Elasticsearch without initializing or clearing it, and does not install dependencies. If startup fails after state is recorded, do not rerun blindly; use `stop` after inspecting its dry-run.

## `stop`

1. Run the workspace's revert script in dry-run mode:

   ```powershell
   pwsh -NoProfile -File '<ticket-workspace>\revert-e2e-env.ps1' -DryRun
   ```

2. Summarize the specific recorded processes and original configuration files it proposes to stop or restore. Ask the user to confirm before stopping processes, restoring files, and removing the workspace E2E state file. If the dry-run refuses because configuration changed, stop; do not overwrite the edits or bypass the check.
3. Only after confirmation, run:

   ```powershell
   pwsh -NoProfile -File '<ticket-workspace>\revert-e2e-env.ps1'
   ```

4. Report the result. The script leaves Elasticsearch and its data untouched and retains the original configuration backups. If no state was recorded, make no changes.
