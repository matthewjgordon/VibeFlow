# Issue Document Template Reference

## Document Header

```markdown
# Feature Issue Breakdown

Source PRD: `path/to/prd.md`

## Issue Summary

- Issue 1 - AFK - Title
- Issue 2 - AFK - Title
- Issue 3 - HITL - Title

## Execution Scope

- Source artifact:
- Output folder:
- Slice validation:
- Implementation report:
- AFK-safe issues:
- HITL issues:
- Blocking HITL:
- Non-blocking HITL:
- Stop before:
- Permission/network/credential/tooling risks:
- Unresolved blockers:
- Relevant wiki pages:
- Wiki guardrails:
- Wiki reconciliation expected:

## Readiness Review

- Resolved in this document:
- Blocking:
- Non-blocking follow-up:
- Converted to HITL issue:
- Converted to stop condition:

## Wiki Reconciliation

- Wiki pages consulted:
- Existing guardrails relevant to this work:
- Planned architectural delta:
- Implemented architectural delta: Not implemented by this issue plan.
- Wiki pages likely requiring updates:
- Reconciliation required: Yes | No
- Reconciliation status: Not started | Not required
```

## Per-Issue Template

```markdown
## Title

## Type

AFK or HITL

For HITL issues, include:

- Blocking status: Blocking | Non-blocking
- Purpose: One sentence explaining why product/user validation is requested

## Goal

Describe the narrow end-to-end behavior, integration path, and architectural
intent.

## Acceptance Criteria

- [ ] Observable outcome
- [ ] Verifiable behavior
- [ ] Testing and architectural expectation

## Validation

- Build:
- Automated checks:
- Manual checks:
- Architectural checks:
- Documentation/reporting:
- Evidence expected:

For HITL validation, write objective product-behavior prompts, not source-code
review or implementation approval requests.

## Stop Conditions

- Stop if:

## Blocked By

List prerequisites or `None - can begin immediately`.

## Notes

Optional implementation constraints, testing expectations, UX considerations,
or future concerns.
```
