# Boilerplate Evolution

This project was created from the reusable AI-assisted development boilerplate maintained at:

wakespace/ai-project-boilerplate

The boilerplate is intentionally treated as a living system.

Its rules, templates, agent roles, and workflow should evolve based on lessons learned while building real projects.

## Current Boilerplate Version

The version used by this project is recorded in:

BOILERPLATE_VERSION

This allows future comparison between the project and newer versions of the boilerplate.

## Improvement Principle

When a problem, limitation, or useful improvement is discovered during project work, determine whether it is:

1. Project-specific.
2. Generally useful across projects.

Project-specific changes belong only in the current project.

Generally useful improvements should be considered for the upstream boilerplate.

## Examples of Boilerplate Improvements

Potential boilerplate improvements include:

- Better agent-role definitions.
- Missing shared rules.
- Confusing or incomplete workflow steps.
- Better task templates.
- Better ADR or specification templates.
- Missing validation rules.
- Better review or QA practices.
- Repeated mistakes caused by unclear instructions.
- Unnecessary process that creates friction.
- Useful conventions that repeatedly apply across projects.
- Better handling of conflicts between documentation.
- Better handoff between Claude, Codex, Gemini, or future agents.

## Agent Responsibility

Agents should notice when a difficulty appears to come from the boilerplate rather than from the project itself.

When this happens, they should explicitly identify it as a potential boilerplate improvement.

Agents must not silently modify the upstream boilerplate from inside a project.

The finding should either:

- Be implemented deliberately in the upstream boilerplate repository, or
- Be recorded as an upstream TODO or GitHub issue for later evaluation.

## Upstream Repository

Canonical upstream repository:

wakespace/ai-project-boilerplate

GitHub Issues in that repository should be used as the persistent backlog for improvements that are identified but not implemented immediately.

## Evaluation Before Upstreaming

Before changing the boilerplate, confirm that the proposed change is broadly reusable.

Ask:

- Would this help more than one project?
- Is the problem caused by the shared workflow or instructions?
- Does the change introduce unnecessary process?
- Can the improvement remain technology-independent?
- Should it be part of the core boilerplate or a future stack-specific preset?

Do not upstream project-specific requirements.

## Versioning

The boilerplate uses semantic-style versioning:

MAJOR.MINOR.PATCH

Guideline:

- PATCH — clarification or small correction without changing the workflow materially.
- MINOR — backward-compatible improvement, new template, new rule, or workflow capability.
- MAJOR — significant change to the development model, project structure, or agent responsibilities.

Projects created from the template keep the version they started with unless deliberately updated.

## Existing Projects

Projects created from an older boilerplate version do not automatically receive newer changes.

When a useful boilerplate improvement is released:

1. Compare the project's current boilerplate version with the newer version.
2. Review the relevant boilerplate changes.
3. Decide whether the change benefits the existing project.
4. Backport only the useful changes.
5. Update the project's BOILERPLATE_VERSION if the project has been brought in line with that version.

Do not blindly overwrite project-specific documentation.

## Feedback Loop

The intended loop is:

Real project
    |
    v
Discover friction, ambiguity, missing rule, or better practice
    |
    v
Determine whether it is project-specific or reusable
    |
    +--> Project-specific: fix locally
    |
    +--> Reusable: propose upstream improvement
                     |
                     +--> Implement now
                     |
                     +--> Record as GitHub issue / TODO
                              |
                              v
                   Improve ai-project-boilerplate
                              |
                              v
                   Release new boilerplate version
                              |
                              v
                 Use in future projects and selectively
                 backport to existing projects

The boilerplate should improve because of real usage, not speculative process design.
