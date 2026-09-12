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
- `docs/adr/` — Architecture Decision Records.
- `docs/specs/` — detailed specifications when required.
- `docs/tasks/active/` — currently authorized units of work.
- `docs/tasks/completed/` — completed task history.

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

The active task defines:

- The goal.
- Context.
- Scope.
- Out of scope.
- Acceptance criteria.

Agents must not silently expand task scope.

Useful work discovered outside the task scope should be recorded as follow-up work rather than implemented automatically.

Acceptance criteria must be treated as observable conditions that require evidence before being considered satisfied.

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
