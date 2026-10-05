# Slice Classification Reference

For each issue, provide:

## Title

Use a short descriptive implementation title.

## Type

Choose `AFK` conservatively only when acceptance criteria and validation are
explicit, no material judgment remains, no unknown credential or permission is
required, and the issue can stop cleanly on failure.

Use `HITL` when unresolved product intent, subjective UX or design,
architectural tradeoffs requiring human authority, manual product acceptance,
or authorization for risky operations requires human judgment. Missing
credentials or tooling are operational blockers, not reasons to delegate
engineering decisions to the human. Resolve technical questions through
project evidence and engineering reasoning before escalating.

For product validation, classify HITL from the product-owner/user perspective:
observable behavior, user experience, workflow correctness, playback, visual
output, available options, and other interaction-level checks.

Do not create HITL issues for implementation details that can be validated by
tests, inspection, or automated checks, such as code organization, object
wiring, class configuration, state propagation, or refactoring correctness.

Default HITL validation to non-blocking unless its outcome determines what
implementation should happen next. Prefer scheduling and batching HITL checks
late enough to allow long uninterrupted implementation runs. Earlier HITL is
appropriate when it materially reduces implementation risk or prevents likely
rework.

Each HITL issue should include a one-line purpose explaining why human product
validation is useful at that point.

## Goal

Describe the narrow end-to-end behavior, intended outcome, and integration path.
Avoid file-by-file implementation detail.

## Acceptance Criteria

Provide concrete observable outcomes, testable behavior, testing expectations,
and architectural expectations.

## Validation

Include relevant builds, tests, manual checks, architectural checks,
documentation requirements, and expected evidence.

Resolve validation guidance in this order:

1. `Slice Validation.md` beside the upstream artifact
2. The repository-wide contributor reference identified by
   `Project Knowledge/Project Knowledge Root.md`
3. An explicit user-provided validation document

State clearly when exact commands remain unknown.

## Stop Conditions

List narrow concrete conditions that stop implementation, including ambiguity,
required approval, missing validation, credentials, network access, failed
prerequisites, broad unrelated refactoring, or worktree conflicts.

## Blocked By

List prerequisite slices or `None`.

## Notes

Optionally record architectural constraints, testing expectations, UX
considerations, and future concerns.
