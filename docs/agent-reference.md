# Agent setup and operating reference

This is the repository-level entry point for adopting and operating VibeFlow.
The starter's [project-local Agent Reference](../starter/Project%20Knowledge/contributor-references/Agent%20Reference.md)
serves a different purpose: working within the adopted project's actual
knowledge environment. Follow that project's documented equivalents after
setup; ordinary project work does not require a dependency back to this repository.

## Initial adoption

When the human authorizes VibeFlow setup, perform ordinary, reversible work
within the granted project/host scope. Resolve routine engineering choices
from evidence and existing conventions. Do not introduce a mandatory setup
proposal followed by a second approval round.

Setup authority does not automatically authorize arbitrary global/system
configuration, remote mutation or publication, destructive operations, unrelated
feature implementation, or decisions belonging to human product authority.
Respect actual access, permission boundaries, and explicit stop conditions.
Ask the narrow question needed for a genuine human decision or missing authority.

### 1. Inspect scope and available context

Read the request, applicable project instructions, and focused documentation.
Determine what the human has authorized and what you can read or write. For an
existing project, inspect relevant source, tooling, and worktree state; preserve
pre-existing edits. For a new idea, work from available intent and context
without assuming a repository, tests, or implementation environment exists.

At the start of `grill-me` or substantial exploration, use the relevant
thinking, decisions, constraints, artifacts, and uncertainties the human has
already supplied; do not make them restate known context. A rough idea is valid.
Use richer relevant context to challenge assumptions, expose gaps, resolve
ambiguity, and sharpen the idea rather than rediscover basics. Help establish
a useful boundary when work is sprawling or ambiguous.

Product-level exploration can be broad. Implementation generally proceeds
iteratively through coherent, bounded features, capabilities, or slices.
Do not infer a request for one enormous PRD, issue plan, or one-shot whole-product
implementation from a broad idea alone. Bounded scope adds no new required
unit or artifact type.

Identify the skills appropriate to this scope; all six are not required.
Use the [workflow and authority guide](workflow.md) for responsibilities and
the [shared dependency contract](adopter-dependencies.md#shared-contract) for
required capabilities and substitutions.

### 2. Make selected skills available

Use the host's supported skill installation/discovery mechanism within the
authorized scope. If the host instead accepts instruction files as context,
provide the selected `SKILL.md` and access to its linked resources. Confirm
availability and invocation rather than assuming copying files made them
discoverable. Consult the host's current documentation when necessary; there
is no universal install command.

Keep each selected skill's complete folder, supporting references, and license
notices together. `to-prd` requires its PRD template; `to-issues` requires its
classification and issue templates. Follow the
[per-skill dependency table](adopter-dependencies.md#per-skill-requirements) and
[attribution/notice guidance](attribution.md#keeping-notices-with-copied-materials).
`grill-me` retains both Matt Pocock's upstream MIT notice and the notice for
Matthew Gordon's additions. Other independently authored materials retain
Matthew Gordon's MIT notice.

[Optional host metadata](adopter-dependencies.md#optional-metadata-and-interfaces)
is distinct from skill behavior; preserve it with the supplied package. Codex,
Claude, Obsidian, Kanban, GitHub, and other hosts/interfaces are optional choices.
Do not require a tracker, plugin, board schema, or orchestration service.

### 3. Establish discoverable maintained knowledge

Discover existing maintained knowledge and useful conventions first. Reuse or
adapt a suitable system instead of creating competing sources. Otherwise copy
the complete `starter/Project Knowledge` folder, including its license, to an
authorized location. Its [root](../starter/Project%20Knowledge/Project%20Knowledge%20Root.md)
and [Contributor Guide](../starter/Project%20Knowledge/contributor-references/Contributor%20Guide.md)
explain the responsibilities; its hierarchy and filenames are starter conventions.

Register the **actual root** through the project's supported agent-instruction
mechanism. Confirm the agent receives the instruction, can follow focused
links, and can write the output areas needed for the selected phases: active
workstreams, implementation reports, reviews, and test evidence. Document
equivalent locations rather than assuming physical folder names. Material
outside the documented knowledge boundary is not automatically maintained
knowledge; follow authoritative references when needed.

Adapt this discovery/upkeep instruction to the actual location:

```text
Maintained project knowledge starts at <actual knowledge-root path>.
Read the root when context is relevant, then follow focused links.
Consult applicable validation before implementation. Update durable knowledge
and navigation when verified changes make them stale. Distinguish intended
behavior from implemented facts and validation evidence. Resolve engineering
questions from project evidence before asking me; ask about genuine unresolved
product intent, preferences, experience, or decisions requiring my authority.
```

Follow [storage and history guidance](workflow.md#interfaces-and-storage):
knowledge may live inside or outside the application's Git repository. Use
appropriate versioning or backup, preserve useful history, and identify
superseded plans. VibeFlow prescribes no universal archival policy.

### 4. Document validation readiness

For an existing project, inspect actual build/test/validation mechanisms during
setup. Populate its validation reference with real commands or procedures,
working directories, environment/prerequisites, required evidence, and failure
gates. Mark inapplicable checks with reasons; resolve genuine missing product
criteria with the human. Use the starter's
[Validation scaffold](../starter/Project%20Knowledge/contributor-references/Validation.md)
when appropriate.

For a new idea without implementation tooling, record validation needs and
defer configuration. Exploration, `grill-me`, PRD work, and appropriate planning
can proceed. Before actual implementation, establish the applicable technical
contract and the environment to run it. `Not configured` is legitimate during
setup but is neither a command nor a passing result. Never invent commands or
environments or silently weaken required checks.

Use [validation resolution](adopter-dependencies.md#validation-resolution)
for the exact discovery order and the bridge for an external user-provided
contract. Planning does not automatically create `Slice Validation.md`.
Record the selected contract path in the issue plan and implementation report.

### 5. Report the setup outcome

Briefly identify available skills, the actual knowledge root and discovery
mechanism, authorized writable destinations, validation readiness, legitimately
deferred needs, and any genuine blocker or human decision. Do not label a
copied scaffold implementation-ready. Stop dependent work on a blocker; a
deferred implementation environment does not block authorized exploration.
Setup alone does not initiate unrelated feature work or the next skill phase.

## Ongoing operation: choose the relevant route

Read focused project knowledge and only the skill/resources needed for the
requested phase. These sources own the detailed rules; this entry routes to
them rather than replacing their procedures.

| Need | Canonical guidance |
| --- | --- |
| Human/agent authority, AFK/HITL, blocking/non-blocking checkpoints, technical validation versus human acceptance | [Workflow and authority](workflow.md#decisions-and-execution), including [terminology](workflow.md#primary-chain) and [validation/acceptance](workflow.md#validation-and-acceptance) |
| Dependencies, supported substitutions, writable outputs and access | [Shared contract](adopter-dependencies.md#shared-contract) and [per-skill requirements](adopter-dependencies.md#per-skill-requirements) |
| Validation discovery, external-contract bridge and missing-check gates | [Validation resolution](adopter-dependencies.md#validation-resolution), the actual project contract, and [implement-issues](../skills/implement-issues/SKILL.md#required-inputs) |
| Canonical reporting, original creation date, resume and disambiguation | [Output/resume conventions](adopter-dependencies.md#output-and-resume-conventions) and [implement-issues report rules](../skills/implement-issues/SKILL.md#4-resolve-and-initialize-the-report) |
| Maintained boundary, source/history expectations, navigation and stewardship | The adopted knowledge root and project-local Agent Reference; starter [source/authority guidance](../starter/Project%20Knowledge/Project%20Knowledge%20Root.md#sources-and-authority), [knowledge conventions](../starter/Project%20Knowledge/wiki/Knowledge%20Conventions.md), and [wiki-update source hierarchy](../skills/wiki-update/SKILL.md#source-hierarchy) |
| Optional host metadata and interfaces | [Metadata guidance](adopter-dependencies.md#optional-metadata-and-interfaces) |

## Skill handoffs

For substantial or ambiguous work, the usual route is
`grill-me → to-prd → to-issues → implement-issues`, with active knowledge upkeep
and `wiki-update` when reconciliation warrants it. A deliverable normally
supplies the next phase's input/context; **it is not authorization** to start
that phase. Honor the human's actual scope, including any authorized multi-phase
work. Preserve issue-breakdown approval and readiness checks without adding
routine engineering approval gates.

The handoffs below describe the supplied skills' output conventions. Resolve
workstream, planning, report, review, and validation locations through the
project's documented knowledge root; do not impose the starter's physical
folders or hierarchy on another maintained system. Documented adopter
equivalents remain valid where the skills and dependency contract allow them.
Required support files, validation discovery, and canonical report naming and
resume rules still apply.

| Phase | Input/context | Deliverable and next use |
| --- | --- | --- |
| [grill-me](../skills/grill-me/SKILL.md) | Idea/conversation, available artifacts, source and focused knowledge when available | A named workstream folder with a same-name Markdown decision artifact: locked Q&A/decisions, constraints, scope, unknowns, validation notes, and reconciliation handoff. Normally context for `to-prd` |
| [to-prd](../skills/to-prd/SKILL.md) | Shared understanding or alternative sufficient context; [PRD template](../skills/to-prd/references/prd-template.md) | Markdown PRD, normally beside its upstream artifact: intended behavior, settled decisions, `Implementation Readiness`, blockers, validation expectations, and `Wiki Reconciliation`. Useful to `to-issues` |
| [to-issues](../skills/to-issues/SKILL.md) | PRD/plan/context; [classification](../skills/to-issues/references/slice-classification.md) and [issue template](../skills/to-issues/references/issues-template.md) | Ordered Markdown slices with dependencies, `Issue Summary`, `Execution Scope`, `Readiness Review`, acceptance/validation, stop conditions, reporting expectations, and reconciliation. Reviewed until approved; input to authorized `implement-issues` |
| [implement-issues](../skills/implement-issues/SKILL.md) | Explicitly identified Markdown issue plan, discoverable validation contract, editable source/tooling and relevant knowledge | Implemented work and per-slice technical evidence in a resumable `YYYY-MM-DD <Workstream Name> Report.md`; actual architectural delta, gaps and reconciliation needs support knowledge maintenance |
| [wiki-update](../skills/wiki-update/SKILL.md) | Current source, reports for rationale, existing wiki/navigation, relevant plans/reviews and handoffs | Reconciled durable concepts and navigation, with a maintenance summary and hygiene findings. No mandatory separately named wiki report; maintained understanding feeds later work |
| [architectural-health-review](../skills/architectural-health-review/SKILL.md) | Current source, relevant knowledge and scoped evidence | `YYYY-MM-DD Architecture Health Review.md` in the documented review area. Periodic side path outside the required linear chain; recommendations do not authorize implementation |

The conceptual chain has important qualifications:

- Planning phases accept alternative sufficient context. Small, clear work may
  bypass the planning chain and be implemented directly without invoking
  `implement-issues` or creating an issue document. If `implement-issues` is
  invoked, that skill requires an explicitly identified issue document. Direct
  work still follows applicable inspection, technical validation, knowledge-upkeep,
  authority, and human-acceptance requirements.
- An artifact can contain blockers. Producing a PRD or plan does not guarantee
  readiness. Follow actual skill output conventions; illustrative PRD/issue
  filenames are not universal required names. Planning artifacts normally share
  the workstream folder, while the durable report uses the documented report area.
- Technical validation runs throughout implementation, one slice at a time,
  before progression. Failed required checks, missing prerequisites, explicit
  stop-before points, and blocking dependencies retain their gates.
- Human acceptance remains separate and pending until provided. Non-blocking
  HITL may remain pending while unrelated, already-authorized AFK work continues;
  blocking HITL stops dependent progression. Follow the detailed workflow and
  selected skill rather than treating HITL as a universal halt or a technical pass.
- Knowledge upkeep occurs during work, not only at its end. Reconcile verified
  implemented reality even when non-blocking human acceptance is pending.
  Preserve plans as intent and reports as evidence; do not fabricate absent
  history or rationale or present proposed behavior as implemented.

[Human Getting Started](getting-started.md) · [VibeFlow](../README.md)
