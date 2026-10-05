---
name: architectural-health-review
description: Perform a focused architectural reconnaissance and health review across a codebase, producing a dated report in the repository's documented architecture-review area. Use when the user asks for an architecture health review, architectural reconnaissance, architecture risk assessment, ownership/boundary review, orchestration review, runtime/realtime safety review, or future-risk assessment without immediate implementation.
---

# Architectural Health Review

Perform a focused architectural reconnaissance and health review across a codebase.

The goal is to identify architectural pressure points, residual coupling, unclear ownership boundaries, orchestration drift, runtime concerns, future-risk surfaces, and cleanup or hardening opportunities. Do not redesign the system, implement changes, or recommend speculative architecture unless a concrete pressure in the codebase justifies it.

## Core Philosophy

Prefer:
- architectural coherence over architectural novelty
- clarity over abstraction
- explicit ownership over hidden coordination
- bounded systems over generalized systems
- evolutionary flexibility over speculative extensibility
- preserving canonical truth over collapsing information prematurely

Do not recommend event buses, generalized command systems, broad frameworkization, unnecessary service layers, premature infrastructure, or architecture beyond demonstrated complexity unless a concrete architectural pressure clearly justifies them.

Calibrate recommendations to project maturity:
- Early-stage systems: prefer coherence over abstraction.
- Mid-stage systems: prefer boundary hardening and orchestration clarity.
- Mature systems: prefer operational robustness and simplification.

## Constraints

- Do not implement code changes unless explicitly requested.
- Do not perform broad refactors.
- Do not introduce new infrastructure without clear justification.
- Prefer incremental hardening over sweeping redesign.
- Preserve explicit orchestration where practical.
- Avoid speculative architecture.
- Prefer stable ownership boundaries over generalized systems.
- Prefer actionable observations over abstract architectural theory.

## Workflow

1. Establish scope and entry points.
   - Inspect repository structure, documentation, build targets, package manifests, and obvious runtime entry points.
   - Inspect the repository for `Project Knowledge/Project Knowledge Root.md`.
     When present, begin within its documented knowledge area, treat it as the
     authoritative project-knowledge area, and follow its links to the wiki,
     contributor references, and architecture-review location.
   - Read the wiki home, design guardrails, glossary, and focused wiki pages
     relevant to the review.
   - Identify primary orchestration/runtime coordination layers, major domains, UI or presentation surfaces, and runtime-sensitive paths.
   - Prefer local repository evidence over assumptions. Ask the user only when code inspection cannot answer a material question.

2. Map architecture before judging it.
   - Build a lightweight mental map of domains, data/artifact lifecycles, runtime state ownership, and cross-boundary interactions.
   - Note apparent project maturity and match recommendation weight to that maturity.
   - Preserve distinctions between canonical state, derived state, cached artifacts, mirrored UI state, and transient runtime facts.

3. Review the required areas.
   - Cover all review areas below, but keep depth proportional to available evidence and project size.
   - Favor concrete file and symbol references where useful.
   - Separate current risks from future pressure and from acceptable temporary compromises.

4. Generate the report.
   - Write `YYYY-MM-DD Architecture Health Review.md` under the repository's
     documented architecture-review location using the current local date.
   - If the repository does not establish a review location, identify an
     appropriate documentation location through inspection.
   - The report is the deliverable. Do not leave the findings only in chat.

## Review Areas

### 1. Orchestration Health

Review the primary orchestration/runtime coordination layer.

Inspect for hidden coordination, policy ownership drift, God-object tendencies, duplicated runtime authority, and unclear domain interaction flow.

Ask:
- Which responsibilities belong here?
- Which responsibilities appear to be embedded domain logic?
- Are interactions explicit and understandable?
- Are runtime facts gathered centrally and clearly?

Report architectural observations, drift risks, cleanup or hardening recommendations, and severity.

### 2. Runtime State Ownership

Inspect runtime state ownership across major systems and domains.

Review duplicated state, stale derived state, ambiguous authority, synchronization-sensitive state, cache-like state, and mirrored UI/runtime state.

Ask:
- Which system is authoritative?
- Are any states duplicated unnecessarily?
- Are synchronization boundaries clear?
- Are any ownership responsibilities ambiguous?

Report an ownership map, ambiguity concerns, synchronization risks, and cleanup recommendations.

### 3. Runtime / Realtime Safety

Inspect runtime-sensitive paths.

Review allocations in sensitive paths, locking or contention risks, synchronization assumptions, cross-thread ambiguity, hidden runtime costs, scaling concerns, and traversal/update amplification risks.

Do not redesign systems unless necessary. The goal is visibility, risk identification, and hardening recommendations.

Report runtime-risk surfaces, acceptable temporary compromises, future hardening candidates, and severity.

### 4. UI / Runtime Boundary Health

Inspect the separation between UI/presentation, orchestration/runtime, and core domains.

Ask:
- Is presentation shaping runtime architecture?
- Are runtime systems exposing too much internal state?
- Are UI assumptions leaking inward?
- Are boundaries healthy for future evolution?

Consider future pressure from visualization, navigation, inspection, scrubbing, caching, and alternate presentation layers. Do not implement UI features.

Report current strengths, future risks, coupling concerns, and recommended guardrails.

### 5. Domain Boundary Review

Inspect major domain boundaries and responsibilities.

Ask:
- Are domain responsibilities coherent?
- Is ownership duplicated?
- Are systems becoming overly aware of one another?
- Is orchestration explicit?
- Is hidden coupling emerging?
- Are domains leaking implementation details?

Report healthy boundaries, weak boundaries, likely future drift areas, and cleanup or hardening opportunities.

### 6. Artifact / Data Lifecycle Review

Inspect lifecycle ownership for major runtime artifacts and data structures.

Ask:
- Who creates them?
- Who owns them?
- Who invalidates or rebuilds them?
- Are lifecycle guarantees explicit?
- Are stale artifact risks visible?
- Are synchronization assumptions clear?

Report lifecycle observations, ownership clarity, invalidation or rebuild concerns, and future-risk areas.

## Report Format

Create under the repository's documented architecture-review location:

```text
YYYY-MM-DD Architecture Health Review.md
```

Use this structure:

```markdown
# Architecture Health Review - YYYY-MM-DD

## Executive Summary

[Overall architecture assessment, strongest architectural qualities, largest remaining risks, apparent maturity assessment, and overall architectural coherence assessment.]

## Architectural Strengths

[Successful extractions, healthy ownership boundaries, deterministic systems, strong orchestration patterns, clean runtime boundaries, and notable areas of architectural health.]

## Pressure Points / Risks

### [Issue Title]

- **Category:** [orchestration drift | ownership ambiguity | runtime/realtime risk | synchronization concern | UI/runtime coupling | stale state | architectural residue | scaling concern | future feature pressure]
- **Description:** [Concrete observation grounded in repository evidence.]
- **Why it matters:** [Practical architectural consequence.]
- **Affected systems:** [Files, modules, domains, or runtime paths.]
- **Severity:** [Low | Medium | High | Critical]
- **Urgency:** [Now | Soon | Later | Watch]
- **Recommended next action:** [Incremental next step, not a speculative redesign.]

## Recommended Workstreams

[Possible future workstreams such as cleanup, hardening, focused extraction, testing expansion, synchronization refinement, runtime-path hardening, or orchestration simplification. Do not assume every recommendation is immediate.]

## Explicit Non-Recommendations

[Premature abstractions, systems that appear sufficiently healthy, areas that should not yet be generalized, and architecture directions likely to overcomplicate the current project stage.]

## Wiki Reconciliation

- Wiki pages consulted:
- Existing guardrails relevant to this review:
- Wiki statements that appear stale:
- Wiki pages likely requiring updates:
- Reconciliation required: Yes | No
```

## Reporting Guidance

- Lead with evidence and architectural consequence.
- Keep severity and urgency distinct: a severe issue may be low urgency if the triggering future pressure is distant.
- Identify current strengths as well as risks.
- Include explicit non-recommendations to prevent overcorrection.
- Make recommendations incremental, bounded, and reviewable.
- Avoid abstract architectural theory unless tied directly to a concrete codebase observation.

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
