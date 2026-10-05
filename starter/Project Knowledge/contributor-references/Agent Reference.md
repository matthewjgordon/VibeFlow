# Agent Reference

## Before working

Read the [knowledge root](../Project%20Knowledge%20Root.md) when project context
is relevant. Follow focused links to vocabulary, architecture, guardrails,
current contributor guidance, and the applicable workstream. Inspect source
and current worktree state before implementation; preserve unrelated changes.

Use the project's documented locations and command contracts. If the expected
root is absent, discover existing conventions before choosing destinations.
An equivalent maintained knowledge system is valid; a missing exact filename
does not remove the responsibility to consult and maintain durable knowledge.

## Resolve and escalate

Autonomously resolve questions answerable through repository inspection,
maintained knowledge, architecture, documentation, tests, engineering reasoning,
or established project conventions. State meaningful assumptions and evidence.

Ask the human about unresolved product intent, preferences, subjective
experience, or tradeoffs requiring human authority. Do not ask the human to
perform technical investigation the agent can reasonably perform. Preserve
scope, authorization boundaries, genuine blocking conditions, and explicit
stop-before points.

## Validate and report

Read [Validation](Validation.md) and any workstream-specific contract. Prefer
CLI/programmatic validation when it reliably establishes the technical
behavior. Use graphical interaction when genuinely necessary or explicitly
requested. Keep checks proportional to scope and risk.

Record the exact relevant checks, actual results, skipped checks with reasons,
limitations, and evidence. Never claim a check passed when it was not run.
Record human experiential/product acceptance separately. A non-blocking human
evaluation can remain pending while later authorized AFK work continues;
blocking gates and dependent decisions still stop progression.

## Maintain knowledge

When verified changes invalidate durable knowledge, update the affected concept
pages and navigation. Capture responsibilities, relationships, rationale,
constraints, and intentional flexibility. Keep plans as intent and reports as
evidence; do not claim an unimplemented design as current architecture.

Use implementation reports to recover rationale and source to verify current
behavior. If a reconciliation gap cannot be resolved, record exactly what is
uncertain and which evidence or authority is needed. Do not silently leave
contradictory context or fabricate missing rationale.

Create new conceptual pages only when there is useful durable content to
maintain. Keep deferred concepts visible as text with a disposition instead
of adding empty pages or broken links. Do not perform unrelated product work
merely because a review recommends it.
