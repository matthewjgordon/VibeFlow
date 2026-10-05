# Example: search a reading list

This fictional example illustrates the handoffs. No sample application is
included, and the results below are illustrative, not claims of executed tests
or accepted product behavior.

Imagine an existing local reading-list app. You can save and browse articles,
and now want to find one quickly. This is more ambiguous than changing a label:
search scope, matching behavior, and the empty state need decisions.

## Explore with grill-me

```text
Help me explore search for our reading list using grill-me.
Inspect the existing list and relevant knowledge first.
Ask about product decisions the project evidence does not resolve.
Use the workstream name Reading List Search and record the decisions.
Do not implement it yet.
```

The agent inspects the existing article model, list behavior, and documentation.
It can determine where titles and tags live without asking you. It asks one
focused product question at a time: for example, whether searches should match
titles alone or tags as well.

Suppose you choose title and tag matching, case-insensitive substring search,
a visible no-results message, and clearing the query to restore the full list.
The decision artifact records those choices, scope, constraints, remaining
questions, and validation expectations. It does not claim that search exists.

## Turn understanding into a PRD

```text
Use to-prd to turn the Reading List Search decisions into a PRD.
Preserve the agreed behavior and classify remaining readiness questions.
Keep the initial scope local; do not add remote indexing or fuzzy ranking.
```

The PRD states the user problem, expected behavior, and boundaries. It identifies
testable outcomes: case-insensitive matching, title/tag coverage, clear-query
restoration, and no-results behavior. Existing architecture and engineering
reasoning determine the smallest suitable integration rather than returning
routine design work to the human.

The PRD marks human evaluation of the search experience as distinct from those
technical checks. It names the applicable validation reference and records
which durable list-behavior explanation will need reconciliation.

## Decompose into implementation work

```text
Use to-issues to propose thin vertical slices from the approved PRD.
Include acceptance criteria, dependencies, the actual validation contract,
the canonical report path, and explicit blocking/non-blocking checkpoints.
```

One possible sequence is:

| Slice | Type | Observable outcome and gate |
| --- | --- | --- |
| Search titles | AFK | Query input filters the real list by title; matching and clear-query checks pass |
| Include tags and no-results behavior | AFK | Search covers both fields, displays the agreed empty state, and preserves existing list behavior; relevant checks pass |
| Evaluate the experience | HITL, non-blocking | Human assesses whether search and recovery feel clear; acceptance stays pending until feedback is supplied |
| Reconcile durable knowledge | AFK | Source-backed list-behavior documentation and navigation reflect what was actually implemented |

AFK means bounded work suitable for autonomous execution with explicit criteria
and feedback. HITL means a genuine human judgment or acceptance point. Review
and approve the breakdown before requesting implementation. If experience
feedback will determine a later slice, make that checkpoint blocking instead.

## Implement and technically validate

```text
Use implement-issues to implement the approved AFK scope in order.
Read the identified validation contract, validate each slice before the next,
and maintain the existing dated report for Reading List Search.
Prepare the non-blocking human evaluation handoff and leave acceptance pending.
Continue the later authorized documentation slice after its dependencies pass.
```

The agent checks the worktree and tooling, initializes or resumes the canonical
report, implements one slice, and runs the actual project checks specified by
the validation contract. Those commands come from the project, not this
example. Required failures must be fixed or recorded as blockers before
dependent implementation progresses.

A report might distinguish:

```text
Technical validation: applicable build and focused matching/integration checks passed.
Human acceptance: pending; query input, clearing, and no-results experience ready to review.
Knowledge reconciliation: completed against implemented source.
```

These are illustrative statuses only. A passing build does not make the search
experience accepted. Non-blocking acceptance does not stop the already-authorized
documentation slice; unresolved feedback that changes subsequent implementation
would stop that dependent work.

## Maintain durable understanding

Use `wiki-update` if the reconciliation needs its fuller maintenance workflow.
The agent verifies current source, uses the report for rationale, and updates
the existing list-behavior page and links. It records the supported search
semantics and deliberately excluded ranking behavior without copying the PRD
or creating a page for every function.

The report retains validation evidence and pending acceptance. The wiki explains
the implemented system. Later, a periodic `architectural-health-review` can
assess actual coupling or performance pressure without automatically introducing
a search framework or authorizing a rewrite.

For a smaller correction, such as making an already-agreed empty-state message
accurate, a direct contextualized request and focused validation are sufficient.
