# Project Bootstrap Status

Status: NOT_STARTED

This file exists only while the project is in bootstrap mode.

Allowed values:

- `NOT_STARTED` — project initialization has not begun.
- `IN_PROGRESS` — project discovery and foundational documentation are being refined.

When initialization begins, Claude Code should change the status to:

`Status: IN_PROGRESS`

There is intentionally no `COMPLETE` state.

Initialization is complete only when the exit criteria in `docs/INITIALIZATION.md` are satisfied and bootstrap finalization has removed this file.

The existence of `PROJECT_STATUS.md` is therefore the bootstrap marker:

- File exists → bootstrap mode is active.
- File does not exist → normal task-driven project mode.

Do not delete this file merely to bypass initialization requirements.

## Canonical Boilerplate Exception

In the canonical repository:

`wakespace/ai-project-boilerplate`

this file intentionally remains present because it must be distributed to newly generated projects.

Its presence does not block maintenance of the boilerplate repository itself.
