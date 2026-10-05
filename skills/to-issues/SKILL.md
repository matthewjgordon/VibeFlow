---
name: to-issues
description: Break a plan, feature, PRD, or architectural concept into independently-grabbable implementation issues using thin vertical slices, with explicit execution scope, AFK/HITL classification, validation gates, stop conditions, and readiness checks suitable for later implement-issues execution. Use when the user wants to convert an idea, PRD, or to-prd output into actionable implementation tasks suitable for human developers and/or coding agents.
---

# To Issues

Break a feature, PRD, or architectural concept into independently-grabbable implementation issues using vertical slices ("tracer bullets").

This skill is intentionally:
- tooling-agnostic
- issue-tracker-agnostic
- LLM-agnostic

The output may later be:
- GitHub Issues
- Jira tickets
- Linear tasks
- markdown issue files
- Obsidian notes
- JSON/YAML work items
- or any other task-tracking system

This skill focuses on:
- decomposition
- dependency mapping
- implementation sequencing
- architectural coherence
- feedback-loop optimization
- implementation-readiness classification
- validation and stop-condition clarity
- uninterrupted implementation flow where safe

NOT:
- issue tracker automation
- workflow orchestration
- repository mutation
- autonomous implementation

---

# Core Philosophy

Large implementation efforts should NOT be decomposed horizontally.

Avoid:
- database-only phases
- backend-only phases
- frontend-only phases
- service-only phases
- UI-only phases

Instead, break work into thin end-to-end vertical slices ("tracer bullets") that:
- cut through all required layers
- produce demonstrable progress
- create early feedback loops
- remain small enough for reliable implementation

Each slice should:
- fit comfortably within an LLM's "smart zone"
- minimize context complexity
- be independently reviewable
- be testable in isolation

---

# Definitions

## Vertical Slice / Tracer Bullet

A thin implementation path that touches every required layer for a narrow piece of functionality.

Examples:
- state model + service integration + minimal UI
- persistence + API route + verification test
- backend logic + rendering + validation

NOT:
- "Implement entire backend"
- "Build all UI"
- "Refactor entire architecture"

A tracer bullet exists primarily to:
- validate architecture
- validate assumptions
- create fast feedback loops
- expose integration problems early

---

## HITL

Human-In-The-Loop.

A task requiring:
- unresolved architectural tradeoffs requiring human authority
- subjective UX review
- design preferences
- product tradeoffs
- ambiguous product intent that project evidence cannot resolve

These tasks should NOT be fully delegated autonomously.

For product validation, treat the human as the product owner and user. HITL
validation should focus on observable product behavior and user experience, not
source-code review or implementation approval.

---

## AFK

Autonomous-agent-friendly work.

Tasks that:
- are clearly bounded
- have strong acceptance criteria
- have reliable feedback loops
- are low-risk to implement autonomously

These tasks are suitable for:
- coding agents
- background implementation
- iterative autonomous execution

---

# Process

## Repository Knowledge Discovery

If repository context exists:
- inspect the repository for `Project Knowledge/Project Knowledge Root.md`
- read it when present
- begin within the root's documented knowledge area and treat it as the
  authoritative project-knowledge area
- follow its links to the wiki, contributor references, architecture reviews,
  active-workstream location, and validation guidance
- read the wiki home, design guardrails, glossary, and only focused wiki pages
  relevant to the work
- preserve wiki terminology and turn relevant guardrails into validation checks
  or stop conditions

If no project-knowledge root exists, inspect repository documentation
conventions before choosing output or validation paths. Do not assume a
physical folder name.

## 1. Gather Context

Work from:
- the current conversation
- a feature request
- a PRD
- a design document
- an architecture discussion
- an issue
- a markdown file
- repository context
- or any combination of the above

If repository context is available:
- explore the codebase
- identify architectural boundaries
- identify relevant modules/services/systems
- identify existing terminology and domain vocabulary
- identify available build/test/validation commands where practical
- identify documentation files used as architectural or validation references

Respect:
- existing architecture
- existing abstractions
- existing naming conventions
- ADRs or architecture notes if present

---

## 2. Consume PRD Readiness

When the input is a PRD, especially one produced by `to-prd`, read its `Implementation Readiness` section before drafting issues.

Extract:
- resolved decisions
- open questions blocking implementation
- open questions not blocking implementation
- HITL gates
- validation expectations
- unattended implementation scope

If the PRD lacks `Implementation Readiness`, infer these categories from the whole PRD and make the inferred readiness explicit in the issue document.

Do not leave unresolved PRD questions as loose review questions in a final issue document intended for implementation. Convert each unresolved question into one of:
- a resolved decision in the issue document, if context clearly supports it
- a blocking question in `Readiness Review`
- a HITL issue
- a per-issue `Stop Conditions` entry
- a non-blocking follow-up concern

If an unresolved question materially affects behavior, UX, architecture, validation, persistence, data shape, external services, or operational risk, do not classify dependent implementation as AFK.

---

## 3. Identify Architectural Boundaries

Before creating implementation slices, identify:

- major systems involved
- ownership boundaries
- deep modules
- integration points
- feedback-loop boundaries
- testing boundaries
- HITL decision boundaries
- AFK-safe execution boundaries

Prefer:
- extending existing deep modules
- preserving architectural cohesion
- small public interfaces
- encapsulated complexity

Avoid:
- shallow utility sprawl
- excessive cross-module coupling
- implementation leakage
- broad refactors disguised as features

---

## 4. Draft Vertical Slices

Break the work into thin independently-grabbable vertical slices.

Each slice should:
- deliver meaningful end-to-end progress
- create observable behavior
- be testable
- remain narrow in scope
- preserve architectural clarity
- include an explicit validation path
- define stop conditions when ambiguity remains

Each slice should ideally:
- touch every required layer
- include validation/testing
- produce something demoable or reviewable

Prefer:
- many thin slices
- narrow scope
- fast feedback
- iterative expansion

Avoid:
- giant implementation batches
- large hidden integrations
- broad architectural rewrites
- phase-based decomposition

---

# Vertical Slice Rules

## Required

Each slice should:
- represent a narrow but complete implementation path
- produce observable or testable behavior
- include acceptance criteria
- minimize context size
- be independently understandable

---

## Preferred

Prefer slices that:
- reduce uncertainty early
- validate architecture quickly
- establish reusable patterns
- expose integration risk immediately

---

## Avoid

Avoid slices that:
- only touch one layer
- defer integration until late phases
- hide complexity
- require massive context
- depend on large speculative rewrites

---

# 5. Classify Each Slice

Read [references/slice-classification.md](references/slice-classification.md) before drafting slices.

When placing HITL issues, optimize for minimizing unnecessary interruptions.
Prefer implementation-complete over implementation-paused.

Use this as a preference, not a hard constraint:
- schedule HITL validation as late in the implementation sequence as reasonably
  possible
- batch related product validations into one HITL issue when practical
- continue planning later AFK work after a HITL issue unless the HITL outcome
  could reasonably change the implementation direction
- treat HITL as non-blocking unless there is a compelling engineering reason
  that validation must occur before more implementation
- reserve mid-implementation pauses for cases where the validation outcome
  genuinely determines what should be built next

If an implementer can safely complete most of the work before product
validation, plan the sequence so they can do that. Do not create HITL work for
validation the user will inevitably perform before accepting the slice, trivial
checks, or implementation details that can be validated through tests,
inspection, or automated validation.

Good HITL candidates are observable product checks such as:
- whether playback still produces audio
- whether a dropdown contains expected options
- whether a visualization appears correct
- whether a workflow behaves as intended from the user's perspective

Poor HITL candidates are implementation checks such as:
- internal code organization
- class configuration
- object wiring
- state propagation
- refactoring correctness

Each HITL issue should include:
- whether it is blocking or non-blocking
- a one-line purpose explaining why product validation is useful at that point
- objective validation prompts wherever possible

---

# 6. Add Issue Summary And Execution Scope

At the beginning of every generated Issues document, include a concise
`Issue Summary` listing every issue, its type, and its title.

Example:

```markdown
## Issue Summary

- Issue 1 - AFK - Engine State Normalization
- Issue 2 - AFK - Persistence Validation
- Issue 3 - HITL - Verify Updated Dropdown Behavior
- Issue 4 - AFK - Documentation
```

Before the numbered issues, include an `Execution Scope` section after the
summary.

The section should state:
- source PRD path or source artifact path
- output folder, usually the same folder as the source PRD or upstream artifact
- validation document path, preferring `Slice Validation.md` in the same folder as the source PRD
- report path expected by later implementation, using the repository's implementation-reports area and the filename `YYYY-MM-DD <Workstream Name> Report.md`; the date is the report creation date, and later implementation runs should continue updating the same report
- AFK-safe issue range or list
- HITL issue range or list
- which HITL issues are blocking vs non-blocking
- stop-before points
- known permission, network, credential, simulator, GUI, or external-system risks
- unresolved blockers, or `None identified`
- relevant wiki pages
- existing wiki guardrails that implementation must preserve
- whether wiki reconciliation is expected after implementation

Use this section to make the document ready for a later `implement-issues` run.

If the intended implementation flow should stop before HITL work, say so
explicitly. If HITL validation is non-blocking, make clear that implementation
can continue through the later planned AFK work.

---

# 7. Add Readiness Review

Before the numbered issues, include a `Readiness Review` section.

Classify every material unresolved question from the PRD or context as:
- resolved in this issue document
- blocking
- non-blocking follow-up
- converted to HITL issue
- converted to stop condition

Do not put unresolved review questions at the bottom of a final issue document without classification.

If there are no unresolved questions, write:

`No unresolved implementation-blocking questions identified.`

---

# 8. Review The Breakdown

Present the proposed slices as a numbered list.

Ask the user:

- Is the granularity appropriate?
- Are any slices too large?
- Are any slices too small?
- Are dependencies correct?
- Should any slices merge?
- Should any slices split?
- Are HITL vs AFK classifications correct?
- Are there architectural concerns not represented?
- Are feedback loops sufficient?
- Is the AFK/HITL execution scope correct?
- Are stop-before points correct?
- Are HITL checkpoints late and batched where practical?
- Are HITL checkpoints correctly marked blocking or non-blocking?
- Do HITL prompts focus on product behavior rather than implementation approval?
- Are validation commands and manual checks sufficient for implementation?

Iterate until approved.

---

## Wiki Reconciliation

Carry the upstream wiki handoff into the issue document:

- Wiki pages consulted:
- Existing guardrails relevant to this work:
- Planned architectural delta:
- Implemented architectural delta: Not implemented by this issue plan.
- Wiki pages likely requiring updates:
- Reconciliation required: Yes | No
- Reconciliation status: Not started | Not required

If a slice would change an existing guardrail without prior approval, classify
it as HITL or add a stop condition.

---

# 9. Output Format

The default output should be saved as a markdown file in the same folder as the upstream document it references.

Prefer this convention:
- If converting a PRD to issues, save the issues document next to that PRD.
- If converting a `grill-me` artifact directly to issues, save the issues document next to that artifact.
- If the upstream artifact lives in an active-workstream folder, save the issues
  document in that folder.
- If no upstream artifact path exists, save the issues document in the
  repository's documented active-workstream area.
- If the feature/workstream does not yet have a folder, ask the user for a name
  and create one under the active-workstream area.

If the repository's active-workstream location has not been established, or if
the correct location is ambiguous, seek clarification from the user before
writing the file.

The output may target:
- GitHub
- Jira
- markdown
- Obsidian
- Linear
- plain text
- JSON
- YAML

Do NOT assume a specific issue tracker unless explicitly instructed.

If no target is specified:
- output markdown issue drafts only

---

# Suggested Templates

Read [references/issues-template.md](references/issues-template.md) before writing the issue document.

---

# Important Principles

- Alignment before implementation
- Small contexts over massive contexts
- Vertical slices over horizontal phases
- Fast feedback loops over large hidden work
- Architectural coherence over raw velocity
- Human judgment over blind autonomy
- Deep modules over shallow module sprawl
- Explicit interfaces over implicit coupling
- Testability is essential for reliable agent implementation

---

## Evidence And Decision Authority

Resolve questions autonomously when repository inspection, maintained project
knowledge, documentation, tests, engineering reasoning, or established
conventions can answer them. Escalate unresolved product intent, preferences,
subjective experience, or tradeoffs that genuinely require human authority.
Technical uncertainty alone is not a reason to require human judgment.

Keep technical validation separate from human product acceptance. Report
pending human acceptance explicitly; passing technical checks does not imply
it. Consult relevant durable knowledge and update it when verified changes
make it stale or contradictory. Record proposed changes as intent and carry
unimplemented documentation changes into the reconciliation handoff.

The named knowledge root, wiki pages, and output folders in this skill are
discovery conventions. Follow documented adopter equivalents when provided;
do not require this exact hierarchy or filename. Preserve the responsibilities,
validation gates, writable outputs, and source-of-truth boundaries.
