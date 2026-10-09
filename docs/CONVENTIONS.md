# Conventions

## General

- Keep implementations simple and explicit.
- Prefer readability over cleverness.
- Avoid premature abstractions.
- Do not implement work outside the current task scope.
- Do not silently change product or architectural decisions.
- Keep documentation synchronized with meaningful changes.
- Prefer small, coherent changes over broad unrelated refactors.

## Language Conventions

Document conventions specific to the project's programming language or languages.

Examples may include:

- Type-system expectations.
- Naming rules.
- Error-handling conventions.
- Module organization.
- Formatting rules.
- Public API conventions.

Remove examples that do not apply and replace them with project-specific rules.

## Framework Conventions

Document conventions specific to the project's framework, platform, or runtime.

Examples may include:

- Component or module organization.
- Server/client boundaries.
- Dependency injection.
- Routing.
- State management.
- Persistence patterns.
- Background processing.

If the project does not use a framework, state that explicitly.

## User Interface Conventions

Document UI conventions when applicable.

Examples may include:

- Styling approach.
- Accessibility expectations.
- Responsive behavior.
- Design-system usage.
- Interaction patterns.

If the project has no user interface, state that explicitly.

## Dependencies

Before adding a dependency:

1. Confirm the existing stack or platform cannot reasonably solve the problem.
2. Explain why the dependency is necessary.
3. Prefer mature and actively maintained dependencies when appropriate.
4. Consider maintenance, security, compatibility, and operational cost.
5. Avoid dependencies that duplicate existing platform capabilities without a clear benefit.

Significant dependency changes may require an ADR.

## Testing

- Test observable behavior rather than implementation details when practical.
- Add tests for important logic, edge cases, and regressions when appropriate.
- A bug fix should include a regression test when the failure can reasonably be automated.
- Tests should be deterministic.
- Avoid depending on external systems in automated tests unless explicitly required.
- Do not weaken or remove valid tests merely to make validation pass.

Project-specific testing strategy should be documented here or in relevant specifications.

## Validation

Before considering implementation work complete, run the relevant checks available for the project.

These may include:

- Automated tests.
- Static analysis.
- Type checking.
- Linting.
- Formatting checks.
- Build or compilation.
- Integration tests.
- End-to-end tests.
- Manual execution or user-facing verification.

If a relevant check does not exist, document that fact instead of inventing a command.

If a check cannot be completed, record why.

Validation failures must not be hidden, bypassed, or misrepresented.

For the repository-based task workflow, Codex records its implementation checks
and results in the task's `task.md`; Claude and Gemini record their own review
and QA evidence in `review.md` and `qa.md`. See `docs/WORKFLOW.md` for report
ownership and handoff rules.

## Git

- Keep commits focused on one logical unit of work.
- Do not mix unrelated changes in the same commit.
- Use a concise commit title followed by a detailed body.
- Commit bodies should document relevant changes, rationale, and validation.
- Additional sections such as Architecture, Risks, Testing, and Follow-up may be included when useful.
- Do not rewrite shared history unless explicitly required and understood.
- Do not discard unrelated local changes.

Recommended detailed commit structure:

<short imperative title>

Changes:
- ...

Rationale:
- ...

Validation:
- ...

Architecture:
- ... when applicable

Risks:
- ... when applicable

Testing:
- ... when applicable

Follow-up:
- ... when applicable

## Documentation

- Repository documentation is part of the implementation.
- Update documentation when a meaningful product, architecture, convention, specification, or workflow change occurs.
- Do not duplicate the same decision across multiple documents unnecessarily.
- Prefer linking to the canonical decision or document.
- Keep historical decisions in ADRs rather than rewriting history without explanation.

## Agent Behavior

Agents should:

- Read `AGENTS.md` before starting meaningful work.
- Read their tool-specific instruction file.
- Read relevant product, architecture, convention, ADR, specification, workflow, and task documents.
- Inspect the existing implementation before modifying it.
- Stay within the active task scope.
- Report missing or conflicting requirements instead of inventing them.
- Preserve existing decisions unless explicitly authorized to change them.
- Record validation evidence accurately.
