# Shared Agent Instructions

This repository is the canonical source of truth for the project.

Do not rely on previous chat conversations, external assumptions, or undocumented context for project decisions.

If information required to complete a task is missing, conflicting, or ambiguous, identify the issue instead of inventing a requirement or silently choosing an interpretation.

## Project Documentation

Before starting meaningful work, agents must consult the relevant repository documentation.

The primary project documents are:

- `docs/PRODUCT.md` — product purpose, users, goals, scope, and product constraints.
- `docs/ARCHITECTURE.md` — system architecture, technical decisions, constraints, and quality goals.
- `docs/CONVENTIONS.md` — implementation, testing, validation, Git, and project-specific conventions.
- `docs/WORKFLOW.md` — development lifecycle and collaboration process.
- `PROJECT_STATUS.md` — temporary marker indicating that bootstrap mode is active.
- `docs/INITIALIZATION.md` — required discovery and project-definition process for newly created projects.
- `docs/BOILERPLATE.md` — boilerplate versioning, feedback, and upstream evolution policy.
- `docs/adr/` — Architecture Decision Records.
- `docs/specs/` — detailed specifications when required.
- `docs/tasks/active/` — currently authorized units of work.
- `docs/tasks/completed/` — completed task history.

## Bootstrap Mode

In generated projects, if `PROJECT_STATUS.md` exists, the project is still in bootstrap mode.

The canonical `wakespace/ai-project-boilerplate` repository is exempt from this gate because it intentionally retains the bootstrap files for distribution.

Before normal task-driven development begins in a generated project, follow `docs/INITIALIZATION.md`.

Claude Code is the default bootstrap facilitator.

Codex and Gemini should not begin normal implementation or QA while bootstrap mode is active unless explicitly assigned initialization-support work.

Bootstrap mode ends only after the initialization exit criteria are satisfied and the temporary bootstrap files are removed.

## General Principles

- Prefer the simplest solution that satisfies the documented requirement.
- Work in small, coherent increments.
- Keep changes focused on the active task.
- Avoid premature abstractions.
- Prefer readability and maintainability over cleverness.
- Inspect the existing implementation before modifying it.
- Do not add dependencies without a clear and documented reason.
- Do not silently change product or architectural decisions.
- Do not implement features outside the current task scope.
- Keep documentation synchronized with meaningful changes.

## Task Discipline

Implementation work should normally be driven by an active task in `docs/tasks/active/`.

New tasks use `docs/tasks/active/NNN-task-name/` with `task.md` as the
approved contract. Create `review.md` and `qa.md` from their templates only
when the corresponding stages begin. Existing completed tasks do not need to be
migrated to this format.

The active task defines:

- The goal.
- Context.
- Scope.
- Out of scope.
- Acceptance criteria.

Agents must not silently expand task scope.

Useful work discovered outside the task scope should be recorded as follow-up work rather than implemented automatically.

Acceptance criteria must be treated as observable conditions that require evidence before being considered satisfied.

Claude owns review evidence in `review.md`; Gemini owns QA evidence in
`qa.md`. Codex records implementation responses and its own validation in
`task.md`. Reports identify their author and model, date, full commit SHA,
relevant working-tree changes, findings, actual checks and results, limitations,
and verdict. Preserve earlier evidence through dated re-reviews/re-tests and
explicit corrections. Read the complete relevant report before responding to
findings; a summary or addendum cannot replace a missing or unreadable report.

Review and QA assignments authorize inspection and validation already
authorized for the task, plus editing the assigned report. Repository edits
remain limited to that report unless separately authorized. Existing
permissions persist; do not ask again for an already-authorized check. Only the
user may authorize skipping a stage, amending the task contract, or closing a
task. Record stage-skip authorization with its date and reason. Closeout moves
the whole task directory and preserves its relative links. See
`docs/WORKFLOW.md` for the complete procedure.

## Architecture Discipline

Implementation decisions that remain within the documented architecture may be made during normal development.

A material architectural change must be explicitly proposed and documented before implementation.

Use an Architecture Decision Record when a decision:

- Changes a major architectural direction.
- Introduces a significant new dependency, service, platform, or integration.
- Changes an established system boundary or responsibility.
- Reverses or replaces a previously documented architectural decision.
- Has meaningful long-term consequences for maintainability, deployment, security, data, or operations.

Agents must not silently override existing ADRs or architectural constraints.

## Source Precedence and Conflicts

Repository documents must be interpreted together rather than treated independently.

Use the following rules:

1. An active task may refine implementation details but must not silently override product or architecture decisions.
2. A specification may clarify behavior but must not silently introduce a material architectural change.
3. A convention governs implementation style but must not override product requirements or architecture.
4. A material architectural change requires an ADR or explicit authorization.
5. If two repository documents conflict, report the conflict instead of choosing one silently.
6. Explicit user instructions for the current task take precedence, but lasting changes should be reflected in repository documentation when appropriate.

## Validation Discipline

Do not consider work complete only because the implementation appears correct.

Use the validation methods appropriate to the project and task.

These may include:

- Automated tests.
- Static analysis.
- Type checking.
- Linting.
- Compilation or build checks.
- Integration tests.
- End-to-end tests.
- Manual execution.
- Browser validation.
- API validation.
- Runtime logs or diagnostics.

If expected validation cannot be performed, record what was not validated and why.

Never hide, bypass, or misrepresent validation failures.

## Agent Roles

Shared project rules live in this file.

Tool-specific roles and operating instructions live in:

- Codex: `CODEX.md`
- Claude Code: `CLAUDE.md`
- Antigravity / Gemini: `GEMINI.md`

Each agent must follow both this file and its tool-specific instructions.

Tool-specific instructions may specialize responsibilities, but they must not override shared project rules.

## Missing Information Policy

Do not invent:

- Product requirements.
- Acceptance criteria.
- Architectural decisions.
- External system behavior.
- Credentials.
- Environment details.
- Validation results.

When required information is missing, state what is missing and why it matters.

When reasonable progress can still be made safely within the documented scope, proceed only with the parts that are supported by repository evidence.

## Boilerplate Feedback

This project may have been created from the reusable `wakespace/ai-project-boilerplate`.

When working on a real project, agents should distinguish between:

- Problems specific to the current project.
- Problems or improvements that may apply to the shared boilerplate.

Potential boilerplate improvements include recurring friction, unclear instructions, missing workflow steps, weak templates, role confusion, validation gaps, or generally useful conventions.

When a reusable improvement is discovered:

1. Explicitly identify it as a potential boilerplate improvement.
2. Do not silently work around the problem as if it were only project-specific.
3. Do not silently modify the upstream boilerplate from within the current project.
4. Recommend either:
   - Updating the upstream boilerplate deliberately, or
   - Recording the improvement as a GitHub issue or TODO in `wakespace/ai-project-boilerplate`.
5. Continue the current project safely when possible without expanding its scope unnecessarily.

Before proposing an upstream change, consider whether it is genuinely reusable across projects.

Consult `docs/BOILERPLATE.md` for the boilerplate evolution and versioning policy.
