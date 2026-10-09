# Workflow Improvement Proposals

## Purpose and Status

This document preserves proposals for later consideration, informed by user-supplied experience using the boilerplate in `real-estate-aggregator`, particularly TASK-003 through TASK-007. The historical task records were not independently inspected for this document, so the observations below are attributed to that supplied experience and are not claims of verified historical evidence. No proposal here is approved or implemented.

The current workflow already records task approvals, validation results, probe evidence, and review/QA commit and working-tree snapshots. These proposals clarify or extend those practices where the reported experience suggests gaps.

## Priority 1: Approval-State Clarity and Pre-Install Guidance

### 1. Explicit task milestones

**Observation (user-supplied project experience):** Status wording can leave it unclear whether the task contract is approved, implementation may begin, review and QA have passed, or closure is authorized. This observation comes from the reported `real-estate-aggregator` experience, especially TASK-003 through TASK-007; no task-by-task attribution is claimed.

**Proposal:** Consider recording separate, dated fields for **contract approved**, **implementation authorized**, **implementation review passed**, **QA passed**, and **closure authorized**, with a short evidence or authorization reference where useful. Keep each field distinct from general task status. This makes the existing state and authorization legible; it must not create new approval gates or change who may authorize a stage. Existing skip rules continue to apply.

**Likely affected documents:** `docs/WORKFLOW.md`, `docs/tasks/TEMPLATE.md`, and possibly `AGENTS.md` if the shared task rules need clarification.

**Benefits and tradeoffs:** Reduces ambiguity in handoffs and task status. Adds a small amount of task-record upkeep and requires clear definitions for not-started, not-required, and passed states.

**Observable adoption check:** A task can show all five milestones and their dates or explicit not-yet/not-required states, and applying the fields to a sample workflow does not introduce an additional authorization step.

### 2. Dependency installation procedure

**Observation (user-supplied project experience):** Reviewing an approval command after installation cannot control lifecycle scripts that already ran during the first install. The concern is recorded from the supplied real-project experience; this document does not independently inspect an installation history.

**Proposal:** Before allowing an install, inspect the proposed dependency versions and their lifecycle scripts. Record the proposed procedure so any required authorization occurs before execution. Keep guidance package-manager-neutral. If an adopted procedure relies on a package-manager option or configuration to defer scripts, verify its exact behavior with the tooling and version in use at adoption; do not treat a later approval command as a pre-install guard.

**Likely affected documents:** `docs/CONVENTIONS.md`, `CODEX.md`, and possibly `AGENTS.md`.

**Benefits and tradeoffs:** Makes install-time execution visible before it occurs. Adds a preflight step, and exact script controls may differ across package managers and versions.

**Observable adoption check:** The documented procedure identifies how versions and lifecycle scripts are inspected, when authorization occurs, and how any execution controls were verified for the adopted tooling.

## Priority 2: Evidence Refinements and Validation Stopping Rule

### 3. Test-first evidence chronology

**Observation (user-supplied project experience):** Final test state alone may not explain whether a test first failed before a fix, was added after the fix, or changed because a fixture or assertion was corrected. This is a reported lesson from the project experience, not an independently verified account of TASK-003 through TASK-007.

**Proposal:** For relevant test-driven work, record dated checkpoints with the test or fixture, command, and actual red/green result. Mark tests added later and state why fixture or assertion corrections were made. Keep historical development evidence distinct from current independent validation. If a historical checkpoint is missing, mark it unavailable; never reconstruct it from the final test state.

**Likely affected documents:** `docs/WORKFLOW.md`, `docs/tasks/TEMPLATE.md`, `docs/tasks/REVIEW_TEMPLATE.md`, and `docs/tasks/QA_TEMPLATE.md`.

**Benefits and tradeoffs:** Makes the development path and strength of evidence easier to assess. Capturing checkpoints takes time, and excessive detail could make routine task reports harder to maintain.

**Observable adoption check:** Where test-first chronology is relevant, the report identifies dated commands and actual outcomes, labels later-added tests and correction reasons, and separates historical evidence from independent checks; missing history is explicitly unavailable.

### 4. Reproducible external probes

**Observation (user-supplied project experience):** A probe result may be difficult to reproduce or judge when its purpose, environment, guards, side effects, or cleanup are absent. This is attributed to the supplied project experience; no probe history was independently inspected.

**Proposal:** When a probe runs, record its purpose, target and environment, command or retained script, applicable authorization and guards, observed results, side effects, cleanup performed, and limitations. Apply this only to probes that run. Do not record secrets; describe necessary secret configuration without copying secret values.

**Likely affected documents:** `docs/WORKFLOW.md`, `docs/tasks/REVIEW_TEMPLATE.md`, and `docs/tasks/QA_TEMPLATE.md`.

**Benefits and tradeoffs:** Improves reproducibility and makes external effects easier to understand. Some probes cannot be replayed safely or exactly, and retaining scripts or outputs needs a suitable project-specific location.

**Observable adoption check:** A report for a task with probes contains the applicable fields and no secret values; a task without probes records that none ran without requiring probe-specific detail.

### 5. Review checkpoint identity

**Observation (user-supplied project experience):** Later comparisons can be unreliable if the reviewed commit and relevant dirty-tree state are unclear. Modification times and line counts cannot prove byte-for-byte equivalence. The current review and QA templates already request a full commit SHA and working-tree summary; this proposal addresses stronger comparisons when needed.

**Proposal:** Preserve the exact commit and relevant dirty-tree state for each checkpoint. When a before/after comparison needs byte-level support, retain a saved diff or hashes of the relevant files. Do not require hashes for every routine review.

**Likely affected documents:** `docs/WORKFLOW.md`, `docs/tasks/REVIEW_TEMPLATE.md`, and `docs/tasks/QA_TEMPLATE.md`.

**Benefits and tradeoffs:** Supports reliable comparison across review or fix checkpoints. Saved diffs or hashes add handling overhead and should be limited to cases where the comparison needs them.

**Observable adoption check:** Each review checkpoint identifies its commit and relevant working-tree state; any claim of byte-for-byte equivalence is supported by a saved diff or relevant file hashes rather than timestamps or line counts alone.

### 6. Validation stopping rule

**Observation (user-supplied project experience):** Validation can expand beyond resolving the task's blockers and required evidence gaps, delaying closure without a concrete remaining risk or required gate. This is a reported process concern, not an independently inspected task history.

**Proposal:** Resolve blockers and required evidence gaps, rerun the checks affected by fixes, and record optional improvements as follow-ups. Broaden validation only when a concrete remaining risk or required gate calls for it. Preserve every existing required check and acceptance criterion.

**Likely affected documents:** `docs/WORKFLOW.md`, `docs/tasks/REVIEW_TEMPLATE.md`, `docs/tasks/QA_TEMPLATE.md`, and possibly `docs/tasks/TEMPLATE.md`.

**Benefits and tradeoffs:** Keeps effort focused while retaining required validation. Applying the rule requires judgment about whether a remaining risk is concrete, so reports should state the reason for added checks.

**Observable adoption check:** The task record shows blockers and required evidence gaps resolved, affected checks rerun, optional work listed as follow-up, and each additional validation step tied to a stated risk or gate; existing required checks remain satisfied.

## Decisions for Later Consideration

- Choose the exact fields and allowed states for the five task milestones, and whether they belong in the task template, workflow, or both.
- Decide how the package-neutral install preflight is expressed; verify any concrete procedure against the package manager and version used when adopting it.
- Decide where test checkpoints, retained probe scripts, diffs, or hashes should live when the evidence is too detailed for a task report.
- Define when a checkpoint comparison needs file hashes or a saved diff; routine reviews should not require hashes.
- Agent automation is deferred until the repository-based report workflow has been exercised. Revisit automation only after that experience provides evidence about which steps are stable enough to automate.
