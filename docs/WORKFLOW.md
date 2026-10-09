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

Meaningful implementation work should normally begin with a task directory in:

`docs/tasks/active/NNN-task-name/`

Copy `docs/tasks/TEMPLATE.md` to the directory as `task.md`. This file is the
approved task contract. The directory gains `review.md` and `qa.md` from their
respective templates only when those stages begin; do not create empty reports
in advance. At those stages, the active directory has this shape:

```text
docs/tasks/active/NNN-task-name/
  task.md
  review.md   # created when review begins
  qa.md       # created when QA begins
```

The task should define:

- Goal
- Context
- Scope
- Out of scope
- Acceptance criteria

`task.md` also records approvals and contract amendments, Codex's own
implementation validation, short report verdicts, and Codex's dated responses
to findings. Add a relative Markdown link to each report when that report is
created. Before then, identify the stage as not started without linking to a
file that does not yet exist.

Only the user may authorize an amendment to the approved contract or its
acceptance criteria. Record the authorization, date, and amendment in
`task.md`, preserving the earlier contract. Review and QA reports provide
evidence against the approved contract; they cannot change it.

Review and QA may be skipped only with explicit user authorization. Record the
authorization, date, and reason in `task.md`, and mark the stage not required.
Do not create a report for a stage that has not started or was authorized as
not required.

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

Codex records its own dated validation checks, commands, actual results,
unexecuted checks, and limitations in `task.md`. Keep detailed review and QA
evidence in their respective reports. Do not present another agent's report
evidence as Codex's own validation.

Do not hide failing checks.

If a relevant check cannot be performed, record why.

## 7. Technical Review

Claude Code is the default independent technical reviewer.

When review begins, Claude creates `review.md` from
`docs/tasks/REVIEW_TEMPLATE.md`. Claude owns the review evidence. The report
must identify the author and model, date, full reviewed commit SHA, relevant
working-tree changes, findings, actual checks and results, checks not run,
limitations, and verdict. Distinguish repository checks, external probes, and
historical or supplied evidence.

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

Keep findings and review evidence in `review.md`. Preserve earlier evidence by
appending dated re-reviews. Explicitly mark findings resolved or superseded;
corrections identify the earlier statement they amend and its replacement.
Handoff names the task-relative report path and gives a short verdict or
blocker summary. The complete report is authoritative; a summary or addendum
does not replace a missing or unreadable report.

Review assignment authorizes repository inspection and validation within
existing task-specific permission, plus editing `review.md`. Repository edits
are limited to that report unless separately authorized. The assignment does
not itself authorize implementation changes, contract amendments, dependency
installation, external-system access, commits, or pushes. Existing permissions
persist; do not ask again for an already-authorized check. Do not fix
implementation findings during review unless separately assigned to do so.

## 8. Integration and QA

Antigravity / Gemini is the default integration and QA agent.

When QA begins, Gemini creates `qa.md` from `docs/tasks/QA_TEMPLATE.md`.
Gemini owns the QA evidence. The report must identify the author and model,
date, full QA commit SHA, relevant working-tree changes, findings, actual
checks and results, checks not run, limitations, and verdict. Distinguish
repository checks, external probes, and historical or supplied evidence.

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

Keep findings and QA evidence in `qa.md`. Preserve earlier evidence by
appending dated re-tests. Explicitly mark findings resolved or superseded;
corrections identify the earlier statement they amend and its replacement.
Handoff names the task-relative report path and gives a short verdict or
blocker summary. The complete report is authoritative; a summary or addendum
does not replace a missing or unreadable report.

QA assignment authorizes repository inspection and validation within existing
task-specific permission, plus editing `qa.md`. Repository edits are limited
to that report unless separately authorized. The assignment does not itself
authorize implementation changes, contract amendments, dependency
installation, external-system access, commits, or pushes. Existing permissions
persist; do not ask again for an already-authorized check. Do not fix QA
findings unless separately assigned to do so.

Do not mark an acceptance criterion as satisfied without evidence.

## 9. Resolve Findings

When review or QA identifies a blocking problem:

1. Codex reads the complete relevant report before responding, changing task
   status, or implementing a fix. A handoff summary or addendum cannot replace
   a missing or unreadable report; report that condition instead of inferring
   the findings.
2. Record a dated Codex response in `task.md`, using the finding IDs and
   stating the disposition. Do not rewrite report evidence or claim another
   agent's finding as independently confirmed.
3. Assign any fix as implementation work and record Codex's own post-fix
   validation, commands, and actual results in `task.md`.
4. Request a re-review or re-test of affected behavior as appropriate. The
   report owner appends evidence; earlier findings and checks remain intact.

Do not expand the original task with unrelated improvements.

Record unrelated discoveries under Follow-up.

## 10. Complete the Task

A task is ready to complete when:

- The documented scope has been implemented.
- Acceptance criteria are satisfied.
- Relevant validation has passed or documented limitations are understood.
- Review has been completed or explicitly authorized as not required.
- Blocking review findings are resolved when review was performed.
- Relevant QA has been completed or explicitly authorized as not required.
- Documentation reflects meaningful changes.

Task closure and moving the directory require explicit user authorization.
Once authorized, record the closure status and date in `task.md`, then move
the directory from:

docs/tasks/active/

to:

docs/tasks/completed/

The completed task becomes part of the project's historical record.

Move the directory as a whole so `review.md`, `qa.md`, and all relative links
remain together. Existing projects adopt this report workflow explicitly;
completed task history does not need to be migrated.

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

Some tasks may not need every optional stage, but skipping review or QA requires
explicit user authorization recorded in `task.md`.

Complex or high-risk tasks may require additional specifications, ADRs, review, or validation.

The important rule is that responsibilities, decisions, scope, and evidence remain explicit.

Report files are created only when their stage begins. Claude owns review
evidence, Gemini owns QA evidence, and Codex records its responses and its own
validation in `task.md`. Assignments permit inspection and validation already
authorized for the task, but repository edits remain limited to the assigned
report unless separately authorized. Existing permissions persist. Only the
user may authorize skipping a stage, amending the approved contract, or closing
the task.

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
