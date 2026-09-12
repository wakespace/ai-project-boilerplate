# Architecture

## Overview

Describe the system at a high level.

Explain what kind of system is being built and the main architectural approach.

## Architectural Goals

Document the qualities the architecture should optimize for.

Examples may include:

- Simplicity
- Maintainability
- Reliability
- Testability
- Security
- Performance
- Portability
- Low operational overhead

Replace these examples with the goals appropriate to the project.

## System Context

Describe the system boundary.

Identify:

- Primary users or actors.
- External systems.
- Important integrations.
- Major inputs and outputs.

Use diagrams when they materially improve understanding.

## Application Stack

Document the approved technologies used by the project.

Include relevant items such as:

- Languages
- Frameworks
- Runtime
- Database
- Hosting or deployment platform
- Package manager
- Testing tools
- External services

Do not add technologies simply because they are common or familiar.

## Major Components

Describe the major components, modules, services, applications, or bounded areas of responsibility.

For each major component, clarify its responsibility and important relationships.

## Data Architecture

Describe how the system stores, reads, writes, transfers, or owns data.

Document when applicable:

- Data stores.
- File formats.
- Data ownership.
- Persistence boundaries.
- Caching.
- Synchronization.
- Data lifecycle.
- Privacy or security constraints.

If the project has no persistent data, state that explicitly.

## Runtime Architecture

Describe how the system behaves when running.

Document when applicable:

- Client/server boundaries.
- Processes or services.
- Background work.
- Network communication.
- Offline behavior.
- Execution environments.
- Deployment topology.

## Integration Architecture

Document important integrations with external systems, APIs, services, devices, or platforms.

For each significant integration, identify:

- Purpose.
- Direction of communication.
- Ownership boundary.
- Failure considerations.

If there are no external integrations, state that explicitly.

## Dependency Principle

Prefer existing platform or language capabilities when they reasonably satisfy the requirement.

Before introducing a significant dependency:

1. Confirm the existing stack cannot reasonably solve the problem.
2. Explain why the dependency is necessary.
3. Consider maintenance, security, compatibility, and operational cost.
4. Prefer mature and actively maintained dependencies when appropriate.

Significant dependency decisions may require an ADR.

## Architectural Constraints

Document decisions or boundaries that implementations must preserve.

Examples may include:

- Required platforms.
- Forbidden dependencies.
- Deployment restrictions.
- Local-first requirements.
- Security boundaries.
- Compatibility requirements.
- Performance limits.

Do not use this section for temporary implementation preferences.

## Quality Attributes

Document the non-functional qualities that materially influence architecture.

Examples may include:

- Reliability
- Availability
- Security
- Performance
- Accessibility
- Maintainability
- Testability
- Observability
- Scalability
- Portability

Define measurable expectations when useful.

## Change Management

Implementation details that remain within the approved architecture do not require an ADR.

Material architectural changes must be explicitly proposed and documented before implementation.

Use `docs/adr/` for decisions that have meaningful long-term architectural consequences.

Agents must not silently change an established architectural decision.
