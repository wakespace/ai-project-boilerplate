# AI Project Boilerplate

A reusable project-governance and AI-assisted development boilerplate.

This repository does not provide an application stack.

Its purpose is to provide a consistent operating structure for projects that use multiple AI agents for architecture, implementation, review, integration, and QA.

## Purpose

Use this boilerplate when starting a new software project that should follow a documented, task-driven, AI-assisted development workflow.

The boilerplate provides:

- Shared AI-agent rules.
- Tool-specific agent responsibilities.
- Product documentation structure.
- Architecture documentation structure.
- Engineering conventions.
- Development workflow.
- Architecture Decision Record templates.
- Specification templates.
- Task lifecycle templates.

Application code, frameworks, libraries, and deployment choices should be defined separately for each project.

## Agent Roles

The default agent responsibilities are:

- Claude Code — technical lead, architecture, planning, and technical review.
- Codex — primary implementation engineer.
- Antigravity / Gemini — integration, QA, and user-experience validation.

Shared rules live in:

AGENTS.md

Agent-specific instructions live in:

CLAUDE.md
CODEX.md
GEMINI.md

## Documentation Structure

Project documentation lives under:

docs/

Main documents:

- docs/PRODUCT.md
- docs/ARCHITECTURE.md
- docs/CONVENTIONS.md
- docs/WORKFLOW.md

Supporting documentation:

- docs/adr/ — Architecture Decision Records.
- docs/specs/ — detailed specifications.
- docs/tasks/active/ — current work.
- docs/tasks/completed/ — completed work history.

Templates are provided for ADRs, specifications, and tasks.

## Project Initialization

A repository created from this template is not immediately ready for implementation.

It starts with:

`PROJECT_STATUS.md` → `Status: NOT_STARTED`

The first phase of every new project is project initialization.

Claude Code is the default initialization facilitator and should:

- Interview the user about the product, users, scope, constraints, data, integrations, and development context.
- Refine `docs/PRODUCT.md`.
- Refine `docs/ARCHITECTURE.md`.
- Refine `docs/CONVENTIONS.md`.
- Propose material technology choices with alternatives and tradeoffs.
- Obtain user approval for important architectural and long-term technology decisions.
- Create initial ADRs when appropriate.

When the initialization interview begins, Claude changes the status to:

`Status: IN_PROGRESS`

When the exit criteria in `docs/INITIALIZATION.md` are satisfied, Claude runs the bootstrap finalization procedure.

Finalization removes the temporary bootstrap machinery, including:

- `PROJECT_STATUS.md`
- `docs/INITIALIZATION.md`
- bootstrap-only instructions from the permanent agent and workflow documents

Only after bootstrap finalization should normal task-driven implementation begin.

See:

- `PROJECT_STATUS.md`
- `docs/INITIALIZATION.md`

## Starting a New Project

The recommended process is:

1. Create a new repository from `wakespace/ai-project-boilerplate`.
2. Clone the generated repository locally.
3. Open the project in the development environment.
4. Start Claude Code from the project root.
5. Ask Claude to begin project initialization according to `docs/INITIALIZATION.md`.
6. Complete the interactive discovery process.
7. Review and approve material product, technology, and architecture decisions.
8. Confirm that `docs/PRODUCT.md`, `docs/ARCHITECTURE.md`, and `docs/CONVENTIONS.md` have been refined for the actual project.
9. Let Claude run the bootstrap finalization procedure in `docs/INITIALIZATION.md`.
10. Confirm that the temporary bootstrap files and instructions have been removed.
11. Create the first active task from `docs/tasks/TEMPLATE.md`.
12. Begin normal task-driven development.

Do not manually copy application-specific assumptions from another project.

Do not begin implementation directly from the generic template documents.

## Default Development Flow

The default flow is:

Project Initialization
    |
    v
Product / Task Definition
    |
    v
Architecture Analysis when needed
    |
    v
Codex Implementation
    |
    v
Validation
    |
    v
Claude Code Review
    |
    v
Gemini Integration / QA
    |
    v
Fix and Revalidate if needed
    |
    v
Task Completion

This is a default responsibility flow, not a mandatory ceremony.

Simple tasks may require fewer stages.

Complex or high-risk tasks may require additional specifications, ADRs, review, or QA.

## Source of Truth

The repository is the canonical source of truth.

Project decisions should be reflected in repository documentation rather than depending on previous chat conversations or undocumented assumptions.

When information is missing or contradictory, agents should report the problem instead of inventing requirements.

## Task Discipline

Meaningful implementation work should normally be driven by an active task in:

docs/tasks/active/

Tasks should define:

- Goal.
- Context.
- Scope.
- Out of scope.
- Acceptance criteria.

When a task is complete, it should be moved to:

docs/tasks/completed/

Completed tasks form part of the project's technical history.

## Architecture Discipline

Routine implementation decisions that stay within the documented architecture do not require an ADR.

Material architectural changes should be documented under:

docs/adr/

Examples include:

- Major architectural direction changes.
- Significant new services or integrations.
- New persistence strategies.
- Important system-boundary changes.
- Replacement of an existing architectural decision.

## Git and Validation

Projects should preserve focused commits with concise titles and detailed bodies.

Validation should use the checks appropriate to the project, such as:

- Tests.
- Static analysis.
- Type checking.
- Linting.
- Build or compilation.
- Integration tests.
- End-to-end tests.
- Manual user validation.

Validation failures should never be hidden or misrepresented.

## Philosophy

The boilerplate exists to make project decisions, scope, responsibilities, and evidence explicit.

It should remain lightweight.

Add process only when it improves clarity, correctness, maintainability, or collaboration.

## Boilerplate Evolution

This boilerplate is intentionally a living system.

Projects created from it should help improve it through real-world use.

Each generated project contains:

- `BOILERPLATE_VERSION` — the boilerplate version the project is aligned with.
- `docs/BOILERPLATE.md` — the feedback, versioning, and upstream evolution policy.

When project work reveals a problem or improvement, determine whether it is project-specific or generally reusable.

Project-specific changes should remain in the project.

Reusable improvements should be considered for the upstream repository:

wakespace/ai-project-boilerplate

If an upstream improvement is identified but not implemented immediately, record it as a GitHub issue so it is not lost.

Existing projects do not automatically receive newer boilerplate versions. Improvements should be reviewed and selectively backported when useful.

The boilerplate should evolve from evidence gathered while building real projects rather than from speculative process design.
