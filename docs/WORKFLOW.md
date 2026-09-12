# Development Workflow

This document defines the default development lifecycle for projects using this repository structure.

The goal is to keep work explicit, reviewable, testable, and easy to transfer between human contributors and AI agents.

## 0. Initialize the Project

A newly created repository starts with generic boilerplate documents and:

`PROJECT_STATUS.md` → `Status: NOT_STARTED`

Before normal task-driven development begins, initialize the project according to:

`docs/INITIALIZATION.md`

Claude Code is the default initialization facilitator.

When the initialization interview begins, Claude should change `PROJECT_STATUS.md` to:

`Status: IN_PROGRESS`

The initialization process should:

- Interview the user to understand the product and problem.
- Identify users, scope, constraints, data, integrations, and operational needs.
- Clarify the current product goal and important exclusions.
- Evaluate technology choices only after relevant requirements are understood.
- Present meaningful technical alternatives and tradeoffs.
- Obtain user approval for material architectural or long-term technology decisions.
- Refine `docs/PRODUCT.md`.
- Refine `docs/ARCHITECTURE.md`.
- Refine `docs/CONVENTIONS.md`.
- Create initial ADRs when appropriate.
- Preserve important open questions that do not block the first task.

Normal implementation should not begin while foundational project documents still contain generic boilerplate placeholders or material unresolved contradictions.

Initialization is ready for finalization when the exit criteria in `docs/INITIALIZATION.md` are satisfied.

Claude should then run the bootstrap finalization procedure defined in `docs/INITIALIZATION.md`.

Finalization removes the temporary bootstrap machinery, including this `## 0. Initialize the Project` section from the generated project's permanent workflow.

Only after bootstrap finalization should the first active task be created.

## 1. Define the Work

Meaningful implementation work should normally begin with an active task in:

docs/tasks/active/

Use:

docs/tasks/TEMPLATE.md

The task should define:

- Goal
- Context
- Scope
- Out of scope
- Acceptance criteria

Do not begin implementation while important requirements are still undocumented or contradictory.

## 2. Clarify Product Behavior

Before implementation, confirm that the task is consistent with:

- docs/PRODUCT.md
- Existing specifications
- Existing product constraints

If product behavior is unclear, resolve the ambiguity before silently choosing an interpretation.

## 3. Evaluate Architecture

For non-trivial work, evaluate whether the task fits within the existing architecture.

Claude Code is the default technical lead and architecture/review agent.

Architecture analysis should consider:

- Existing system boundaries
- Dependencies
- Data flow
- Integration impact
- Security
- Maintainability
- Testing implications
- Operational consequences

If the task requires a material architectural change, create or update an ADR before implementation.

Do not create ADRs for routine implementation details that remain within the approved architecture.

## 4. Prepare Specifications When Needed

Use docs/specs/ when a task requires more detailed behavior or technical definition than fits cleanly inside the task file.

Specifications are useful for:

- Complex workflows
- API contracts
- Data formats
- Integration behavior
- State transitions
- Complex business rules
- Important edge cases

A specification should clarify implementation work without silently changing product or architectural decisions.

## 5. Implement

Codex is the default implementation agent.

Implementation should:

- Follow the active task.
- Respect product and architecture documentation.
- Inspect existing code before editing.
- Make the smallest coherent change that satisfies the task.
- Avoid unrelated refactors.
- Add or update tests when appropriate.
- Keep relevant documentation synchronized.

Implementation notes may be recorded in the task when useful.

## 6. Validate Implementation

Before review, run the relevant validation available for the project.

Examples include:

- Tests
- Type checking
- Static analysis
- Linting
- Formatting checks
- Build or compilation
- Integration checks

Record validation evidence in the task's Validation section.

Do not hide failing checks.

If a relevant check cannot be performed, record why.

## 7. Technical Review

Claude Code is the default independent technical reviewer.

Review the actual implementation and relevant Git diff.

The review should evaluate:

- Correctness
- Task scope
- Acceptance criteria
- Architecture compliance
- Maintainability
- Error handling
- Tests
- Security implications when relevant
- Unnecessary complexity
- Unrelated changes

Review findings should distinguish:

- Blocking issues
- Non-blocking improvements
- Optional follow-up work

Do not silently fix findings during review unless explicitly assigned to do so.

Record relevant findings and resolutions in the task's Review section.

## 8. Integration and QA

Antigravity / Gemini is the default integration and QA agent.

QA should validate observable behavior rather than relying only on code inspection.

Use the validation method appropriate to the project, such as:

- Browser interaction
- Command-line execution
- API requests
- End-to-end tests
- Integration tests
- Manual user workflows
- Runtime logs and diagnostics

Verify the active task's acceptance criteria with evidence.

Record QA findings in the task's QA section.

Do not mark an acceptance criterion as satisfied without evidence.

## 9. Resolve Findings

When review or QA identifies a blocking problem:

1. Record the finding.
2. Assign the fix as implementation work.
3. Re-run relevant validation.
4. Re-review or re-test affected behavior.

Do not expand the original task with unrelated improvements.

Record unrelated discoveries under Follow-up.

## 10. Complete the Task

A task is ready to complete when:

- The documented scope has been implemented.
- Acceptance criteria are satisfied.
- Relevant validation has passed or documented limitations are understood.
- Blocking review findings are resolved.
- Relevant QA has been completed.
- Documentation reflects meaningful changes.

Update the task status and move it from:

docs/tasks/active/

to:

docs/tasks/completed/

The completed task becomes part of the project's historical record.

## 11. Commit the Work

Keep commits focused on logical units of work.

Use the commit conventions defined in:

docs/CONVENTIONS.md

Commit messages should record meaningful context, including changes, rationale, and validation when applicable.

## Default Agent Responsibility Flow

The default responsibility flow is:

Product / Task Definition
    |
    v
Architecture Analysis when needed
    |
    v
Codex Implementation
    |
    v
Automated / Technical Validation
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

This flow is a default, not a rigid ceremony.

Simple tasks may not require every stage.

Complex or high-risk tasks may require additional specifications, ADRs, review, or validation.

The important rule is that responsibilities, decisions, scope, and evidence remain explicit.

## 12. Capture Boilerplate Feedback

Real project work is also a source of feedback about the shared development boilerplate.

During implementation, review, QA, or task completion, consider whether any discovered friction is caused by:

- The current project itself.
- The shared boilerplate, workflow, templates, or agent instructions.

Examples of potential boilerplate findings include:

- An agent repeatedly misunderstands its responsibility.
- A required workflow step is missing.
- A template does not capture information that repeatedly matters.
- A rule is ambiguous or contradictory.
- Review or QA responsibilities overlap poorly.
- Validation requirements are insufficient.
- The process introduces unnecessary friction.
- A generally useful convention is repeatedly rediscovered.

Project-specific findings should remain in the current project.

Reusable findings should be explicitly identified as potential upstream boilerplate improvements.

If the improvement should not be implemented immediately, record it as an issue in:

wakespace/ai-project-boilerplate

Do not silently work around reusable boilerplate problems and allow them to be forgotten.

See:

docs/BOILERPLATE.md

for the complete evolution and versioning policy.
