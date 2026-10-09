# Project Initialization

This document defines the required initialization process for a new project created from this boilerplate.

A newly generated repository contains generic templates rather than a completed project definition.

Before meaningful implementation begins, those templates must be refined for the actual product being built.

## Default Initialization Agent

Claude Code is the default project-initialization facilitator because it also serves as the project's technical lead and software architect.

During initialization, Claude should act as:

- Requirements interviewer.
- Technical discovery facilitator.
- Architecture advisor.
- Documentation author.

Claude must not invent product requirements or silently choose important architectural decisions.

The user remains the source of product intent and approves material decisions.

## Bootstrap Status

Bootstrap state is represented by the existence of:

`PROJECT_STATUS.md`

A newly generated project starts with:

`Status: NOT_STARTED`

When the initialization interview begins, Claude Code should change it to:

`Status: IN_PROGRESS`

There is intentionally no `COMPLETE` status.

Bootstrap mode ends only after the initialization exit criteria are satisfied and the bootstrap finalization procedure removes `PROJECT_STATUS.md`.

The existence of the file is therefore the state signal:

- `PROJECT_STATUS.md` exists → bootstrap mode is active.
- `PROJECT_STATUS.md` does not exist → normal task-driven development mode.

Do not remove the file merely to bypass initialization.

## Initialization Rule

Do not begin normal feature implementation while the project's foundational documents are still generic templates or contain material unanswered questions.

Initialization should establish enough shared context for later agents to work without depending on previous chat conversations.

The goal is not to predict the entire future of the product.

The goal is to establish a sufficiently clear baseline for the current product version.

## Interview Style

Initialization should be interactive.

Claude should:

1. Inspect the repository before asking questions.
2. Identify information already available and avoid asking for it again.
3. Ask questions in small coherent groups rather than presenting an overwhelming questionnaire.
4. Explain why a question matters when the reason is not obvious.
5. Summarize important conclusions periodically.
6. Distinguish confirmed decisions from assumptions, proposals, and open questions.
7. Challenge contradictions or unrealistic constraints when necessary.
8. Avoid prematurely choosing technologies before understanding the problem.
9. Prefer evidence and explicit constraints over fashionable technology choices.
10. Ask follow-up questions when an answer materially affects product or architecture decisions.

## Discovery Areas

The interview should cover the areas that materially affect the project.

Not every project requires every question.

### Product and Problem

Understand:

- What problem is being solved.
- Why the problem matters.
- Who experiences the problem.
- How the problem is handled today.
- What outcome the product should create.
- What the current product version must accomplish.
- What is explicitly out of scope.

### Users and Usage

Understand when relevant:

- Primary users.
- Secondary users.
- User skill level.
- Expected devices and platforms.
- Usage frequency.
- Accessibility needs.
- Connectivity assumptions.
- Geographic or language constraints.

### Product Constraints

Identify meaningful constraints such as:

- Budget.
- Time.
- Existing systems.
- Required platforms.
- Offline or local-first behavior.
- Privacy expectations.
- Regulatory requirements.
- Data ownership.
- Compatibility requirements.
- Distribution restrictions.

### Functional Scope

Clarify:

- Core capabilities.
- Important workflows.
- Critical edge cases.
- External integrations.
- Inputs and outputs.
- What must work in the first usable version.

Avoid designing speculative future features unless they materially affect current architecture.

### Data

Understand when relevant:

- What data exists.
- Where data originates.
- Where data should live.
- Who owns the data.
- Whether persistence is required.
- Synchronization requirements.
- Backup or recovery expectations.
- Retention requirements.
- Sensitive or personal data.

### Security and Privacy

Understand when relevant:

- Authentication requirements.
- Authorization requirements.
- Sensitive information.
- Secrets or credentials.
- Trust boundaries.
- Regulatory or contractual restrictions.
- Threats that materially affect architecture.

### Integrations

Identify:

- External APIs.
- Third-party services.
- Devices.
- File formats.
- Existing systems.
- Webhooks or events.
- Platform APIs.

Clarify failure behavior and ownership boundaries for important integrations.

### Operational Requirements

Understand when relevant:

- Expected scale.
- Availability expectations.
- Performance requirements.
- Deployment model.
- Hosting constraints.
- Observability needs.
- Backup and recovery.
- Cost limits.

Do not introduce enterprise-scale infrastructure without evidence that the project requires it.

### Development Context

Understand:

- Developer experience and preferences.
- Languages or technologies that are required or strongly preferred.
- Existing code or repositories.
- Learning goals when they materially influence technology choice.
- Expected development environment.
- Team size.
- AI-agent workflow expectations.

Preferences should influence decisions, but should not override hard product constraints without discussion.

## Technology Selection

Technology selection happens after enough requirements and constraints are understood.

Claude should not simply choose its preferred stack.

For material technology decisions:

1. Identify the requirements driving the decision.
2. Present a small number of reasonable options when meaningful alternatives exist.
3. Explain important tradeoffs.
4. Recommend an option.
5. Explain why it fits this project.
6. Ask for user approval when the decision materially affects architecture or long-term maintenance.

Technology decisions may include:

- Programming language.
- Framework.
- Runtime.
- Database.
- Persistence strategy.
- Hosting.
- Deployment.
- Authentication.
- State management.
- Testing tools.
- Package manager.
- Styling system.
- External services.

Do not introduce technology merely because it is common, fashionable, or familiar.

## Architecture Definition

After product discovery and technology selection, Claude should define the initial architecture at the level necessary for the current product version.

Consider when relevant:

- System boundary.
- Major components.
- Responsibilities.
- Data ownership.
- Runtime boundaries.
- External integrations.
- Deployment model.
- Security boundaries.
- Important quality attributes.
- Architectural constraints.

Use ADRs for material architectural decisions that deserve a durable decision record.

Do not create ADRs for every routine implementation choice.

## Engineering Conventions

The generic `docs/CONVENTIONS.md` must be refined for the chosen project.

Define when relevant:

- Language conventions.
- Framework conventions.
- Module or component organization.
- Error handling.
- State management.
- Testing strategy.
- Validation commands.
- Formatting and linting.
- UI conventions.
- Dependency rules.
- Project-specific Git practices.

Do not keep irrelevant placeholder sections simply because they exist in the template.

## Required Initialization Outputs

At minimum, initialization should result in a meaningful project-specific version of:

- `docs/PRODUCT.md`
- `docs/ARCHITECTURE.md`
- `docs/CONVENTIONS.md`

Update when necessary:

- `docs/adr/`
- `docs/specs/`
- `README.md`

The initialization process may also identify the first candidate tasks.

## Open Questions

Not every question must be resolved before development begins.

An unresolved question may remain open when:

- It does not block the current product goal.
- It does not force a premature architectural decision.
- Deferring the decision reduces unnecessary speculation.

Important unresolved questions should be documented rather than forgotten.

## Initialization Exit Criteria

Project initialization is ready for bootstrap finalization when:

- The product problem and current goal are clear.
- Primary users are understood.
- Current scope and important exclusions are documented.
- Material constraints are documented.
- The initial technology stack has been deliberately selected.
- Major architectural boundaries are documented.
- Important architectural decisions have ADRs when appropriate.
- Engineering conventions reflect the actual stack.
- Material contradictions between project documents have been resolved.
- Remaining open questions do not block the first implementation task.

Initialization completion does not mean the project can never change.

Product, architecture, and conventions should evolve when real evidence justifies change.

## Finalize Bootstrap

After the initialization exit criteria are satisfied and the user has approved the material product and architectural decisions, finalize bootstrap before beginning normal task-driven development.

Claude Code should:

1. Verify that `docs/PRODUCT.md`, `docs/ARCHITECTURE.md`, and `docs/CONVENTIONS.md` describe the actual project rather than the generic template.
2. Verify that required initial ADRs have been created.
3. Preserve any non-blocking open questions in the appropriate permanent project document.
4. Remove the `## Bootstrap Mode` section from `AGENTS.md`.
5. Remove `PROJECT_STATUS.md` and `docs/INITIALIZATION.md` from the documentation map in `AGENTS.md`.
6. Remove the `## Bootstrap Mode` section from `CLAUDE.md`.
7. Remove the bootstrap-only conditional instruction from Claude's `Before Starting Work` section.
8. Remove `## 0. Initialize the Project` from `docs/WORKFLOW.md`, so the permanent workflow begins with normal task definition.
9. Remove bootstrap-only sections from `README.md`, including `## Project Initialization` and `## Starting a New Project`.
10. Remove the `Project Initialization` stage from the README's default development flow.
11. Remove `PROJECT_STATUS.md`.
12. Remove `docs/INITIALIZATION.md`.

Bootstrap-specific instructions should not remain in the initialized project's permanent agent context or normal development workflow.

After finalization, the repository should contain only the rules and documentation required for ongoing development.

The first active task may then be created and normal task-driven development may begin.

## First Task

After bootstrap finalization, define the first small, coherent, valuable task
in a new directory, using:

```text
docs/tasks/active/NNN-task-name/task.md
```

Copy `docs/tasks/TEMPLATE.md` to `task.md`. Create `review.md` or `qa.md` from
its report template only when the corresponding stage begins. Follow
`docs/WORKFLOW.md` for report ownership, handoffs, and closeout.

The first task should move the project toward a working product rather than creating infrastructure with no demonstrated need.

Normal task-driven development begins after this point.
