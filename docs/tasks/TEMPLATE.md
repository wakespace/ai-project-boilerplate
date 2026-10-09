# Task: [title]

Status: TODO

## Approvals and Contract

Record the user's authorization, approved decisions, and date. Preserve the
original approved contract when amendments are authorized; record each
amendment with its date and approval. Review and QA reports record evidence but
cannot amend this contract or its acceptance criteria.

Record any user authorization to skip review or QA here with the date and
reason. A skipped stage is marked not required under Reports and has no report
file.

## Goal

Describe the outcome this task must achieve.

## Context

Explain why this task exists and any relevant background needed to understand it.

## Scope

- Define what must be implemented.
- Keep the scope explicit and limited.

## Out of Scope

- Define what must not be implemented as part of this task.

## Acceptance Criteria

- [ ] Define observable behavior that must be true when the task is complete.
- [ ] Keep criteria objective and verifiable.
- [ ] Include relevant failure or edge cases when applicable.

## Implementation Notes

Codex records implementation notes here when useful. Do not use this section
to silently introduce requirements that are missing from the approved task.

## Codex Validation Summary

Record Codex's own dated checks, commands, and actual results. Include checks
not run and limitations with the reason. Keep detailed review and QA evidence
in the respective reports.

## Reports

- Review: Not started; create `review.md` from `docs/tasks/REVIEW_TEMPLATE.md`
  when review begins. Once created, link it here using a relative link and
  record its latest verdict and a short summary.
- QA: Not started; create `qa.md` from `docs/tasks/QA_TEMPLATE.md` when QA
  begins. Once created, link it here using a relative link and record its
  latest verdict and a short summary.

When a stage is explicitly authorized as not required, record the user's
authorization, date, and reason above, then mark the stage not required here.
Do not create its report.

## Codex Responses to Findings

Record dated Codex responses to report findings by finding ID, including the
disposition and any fix. Record Codex's post-fix checks and actual results in
the Codex Validation Summary. Do not rewrite report evidence or represent
another agent's finding as Codex's independent confirmation. Read the complete
relevant report before responding; a summary or addendum cannot replace a
missing or unreadable report.

## Closeout

- User authorization to close: [date and authorization]
- Closed on: [YYYY-MM-DD, or `Not closed`]

Only close a task after explicit user authorization. Once authorized, move the
whole task directory to `docs/tasks/completed/`, preserving its directory name
and relative links.

## Follow-up

Record useful work discovered during this task that is intentionally outside its scope.
