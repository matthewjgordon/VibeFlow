# Workflow and authority

VibeFlow combines human-led product authority with agent-executed engineering
and persistent, actively maintained project knowledge. The workflow applies
across coding agents and project-management interfaces.

## Decisions and execution

The human owns product intent, preferences, subjective experience, acceptance,
and unresolved tradeoffs whose meaning requires human authority. The agent
should inspect the repository, relevant maintained knowledge, documentation,
architecture, tests, and established conventions before asking a question.
It should resolve engineering questions autonomously where that evidence and
engineering reasoning support a decision.

An agent should state a material assumption and its evidence, surface a real
tradeoff, or ask the narrow question needed when product meaning remains
unknown. Routine technical uncertainty does not transfer engineering work to
the human. Execution still follows the task's authorization, agreed scope,
permission boundaries, validation gates, and explicit stop conditions.

## Primary chain

1. `grill-me` reduces ambiguity through focused questioning and records locked
   decisions, constraints, remaining questions, and the downstream handoff.
2. `to-prd` synthesizes intended behavior, scope, architecture direction,
   testing decisions, and implementation readiness.
3. `to-issues` decomposes work into thin vertical slices with acceptance
   criteria, dependencies, validation, AFK/HITL classification, and explicit
   blocking or non-blocking human checkpoints.
4. `implement-issues` implements one slice at a time, passes its applicable
   technical gate, and records results in a single resumable dated report.

**AFK** describes bounded work the agent can execute autonomously because the
necessary authority, context, criteria, and validation are available.
**HITL** means human-in-the-loop and marks a point requiring genuine human
judgment, input, authority, or acceptance.

HITL does not inherently stop all work. A checkpoint is **blocking** or
**non-blocking** depending on whether subsequent work depends on its outcome.
Non-blocking HITL may remain pending while unrelated, already-authorized AFK
work continues. Blocking HITL stops dependent progression until the required
human outcome exists.

The skills preserve approval of the issue breakdown and required readiness
checks. Once execution is authorized, do not manufacture additional approval
stops for technical decisions the project evidence resolves. The full chain
is useful for substantial new capabilities; use proportional planning and
validation for smaller work.

## Validation and acceptance

Technical validation checks observable requirements, builds, tests, integration
behavior, documentation, and applicable architectural constraints. Prefer
programmatic checks where they establish the behavior reliably. Human
evaluation covers subjective experience, usability, appearance, preferences,
and product acceptance.

A passed test suite does not imply human acceptance. Record pending human
evaluation honestly. A non-blocking human checkpoint may remain pending while
later authorized AFK work continues. Stop when an explicit blocking checkpoint
or the human outcome determines dependent implementation. Known technical
failures cannot be treated as non-blocking human acceptance.

## Maintained knowledge

The agent consults focused knowledge relevant to its task and updates durable
explanations when verified changes invalidate them. It records implemented
behavior and rationale, maintains navigation, and distinguishes current facts
from proposed, superseded, deferred, or partially implemented work.

`wiki-update` supports this responsibility. `architectural-health-review`
provides periodic technical assessment without automatically authorizing a
redesign or implementation.

The starter hierarchy is one recommended implementation. Its purpose is to
separate durable explanations, current process guidance, planning intent,
implementation evidence, and point-in-time reviews. Adopters can change paths,
names, or the hierarchy while preserving those responsibilities.

## Interfaces and storage

Codex or Claude can implement the coding-agent role. Obsidian can be a
convenient interface over the Markdown files. Kanban, GitHub, or another
tracker can organize work. These are optional interfaces, not prerequisites.
VibeFlow prescribes no card IDs, metadata schema, board columns, or meaning of
Done.

Choose whether the knowledge lives inside or outside the application's Git
repository. Version or back up durable knowledge appropriately, and give the
agent access to its actual location. Decide how to retain, archive, or retire
plans for the project; preserve useful history and prevent obsolete text from
silently becoming authoritative context.
