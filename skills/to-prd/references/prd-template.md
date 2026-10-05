# PRD Template Reference

Use this structure when writing a PRD. Keep sections concise and focused on
behavior, durable architectural decisions, implementation readiness, and the
wiki-maintenance handoff.

## Problem Statement

Describe the user problem, friction, missing capability, and workflow impact.
Avoid implementation detail.

## Solution

Describe intended behavior, expected user experience, system capability, and
high-level architectural direction. Do not sequence implementation here.

## User Stories

Provide a long numbered list using:

`As a <actor>, I want <capability>, so that <benefit>.`

Cover workflows, edge cases, failure states, operational behavior, and
integration behavior where relevant.

## Implementation Decisions

Document durable decisions:

- Candidate modules and systems
- Ownership boundaries
- Interface expectations
- Integration points
- State and persistence rules
- Schema or API contracts
- Interaction flows
- Synchronization and operational assumptions

Avoid transient file paths and low-level implementation scripts. Include a
trimmed protocol, state machine, schema, reducer, or type shape only when it
captures an important architectural decision more clearly than prose.

## Testing Decisions

Document observable behavior, public-interface checks, integration paths,
feedback loops, repository testing patterns, and validation expectations.

## Implementation Readiness

### Resolved Decisions

List behavior, architecture, persistence, validation, and operational decisions
that downstream planning can treat as settled.

### Open Questions Blocking Implementation

For each blocking question, state why it blocks implementation, the affected
capability, and the narrow decision required. Write `None identified.` when
there are no blockers.

### Open Questions Not Blocking Implementation

For each question, explain why implementation can proceed and how to avoid
foreclosing the later decision. Write `None identified.` when empty.

### HITL Gates

List subjective UX judgment, unresolved architectural or product tradeoffs
requiring human authority, external-service decisions requiring authorization,
manual product acceptance points, and irreversible changes that require
approval. Resolve evidence-supported engineering decisions autonomously.
Write `None identified.` when empty.

### Validation Expectations

Describe expected build commands, tests, manual checks, UI or external-system
validation, reporting expectations, and blocking failure conditions. Identify
the contributor reference that must provide unknown commands.

### Unattended Implementation Scope

State what can proceed AFK, what requires HITL, stop-before points, and
permission, network, credential, simulator, GUI, or external-system risks.

## Out Of Scope

List deferred functionality, unrelated improvements, and speculative
expansions.

## Further Notes

Optionally record risks, migration concerns, future extensibility, and
non-blocking tradeoffs.

## Wiki Reconciliation

- Wiki pages consulted:
- Existing guardrails relevant to this work:
- Planned architectural delta:
- Implemented architectural delta: Not implemented by this PRD.
- Wiki pages likely requiring updates:
- Reconciliation required: Yes | No
- Reconciliation status: Not started | Not required

