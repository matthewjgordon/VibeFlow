# Adopter dependencies and substitution points

These skills preserve their working behavior. An adopter supplies
the project-specific resources that make that behavior meaningful. Naming
conventions below are defaults, not a required universal hierarchy.

## Shared contract

| Resource or capability | Adopter supplies | What remains required |
| --- | --- | --- |
| Coding agent | A host that can read context, inspect source when relevant, reason, communicate, and write authorized artifacts | No named host or model; context-only planning can start before a repository exists |
| Human product authority | A reachable product owner and known authorization/scope | Escalate genuine intent, preference, experiential, or unresolved authority decisions |
| Maintained project knowledge | A readable root/index and relevant conceptual/process documents | Consult focused knowledge and maintain it when verified facts change |
| Knowledge discovery | Register the actual knowledge-root location in project instructions | `Project Knowledge/Project Knowledge Root.md` is a starter convention; use documented equivalents |
| Writable output locations | Workstream, implementation-report, architecture-review, and test-evidence areas as needed | Artifacts cannot remain only in chat; destinations must be authorized and unambiguous |
| Repository and history | Current source for source-backed work; Git status/history when available | Preserve pre-existing edits; do not invent absent history or treat plans as current behavior |
| Validation contract | Exact relevant build/test/check commands, environments, acceptance criteria, and failure gates | No invented commands, weakened checks, or claims that an unconfigured template validated implementation |
| Product evaluation | A human evaluation path and explicit blocking/non-blocking checkpoints | Technical results and human acceptance are recorded independently |

If a location, workstream name, validation rule, or decision is already clear
from authorized context, use it. Ask only when inspection and established
conventions cannot resolve an ambiguity that matters. Persistent knowledge is
foundational; a missing named file triggers discovery, not permission to omit
ongoing stewardship.

## Per-skill requirements

| Skill | Necessary inputs and outputs | Preserved dependencies/substitutions |
| --- | --- | --- |
| `grill-me` | Discussable intent/context; human for genuine unknown intent; named writable decision artifact | Source/knowledge inspection when available; active-workstream location and readable name; downstream planning remains separately requested |
| `to-prd` | Conversation or upstream artifact; writable PRD destination | Keep `references/prd-template.md` with the skill; readiness, architectural direction, validation expectations, and knowledge handoff remain in the PRD |
| `to-issues` | PRD/plan/context; writable issue document; approved breakdown | Keep both `references/slice-classification.md` and `references/issues-template.md`; explicit acceptance/validation, AFK scope, HITL blocking status, stop conditions, and report location |
| `implement-issues` | Explicit issue plan; editable source; available engineering tooling; readable validation contract; writable canonical report | Prefer workstream `Slice Validation.md`; otherwise use the repository-wide contributor validation reference. Stop if neither exists or required commands are unresolved. Validate before the next implementation slice |
| `wiki-update` | Existing conceptual knowledge and navigation; source-backed implemented change or review scope; rationale evidence when available | Ordinary Markdown relative links replace editor-specific links; follow actual page layout, preserve concepts, report graph hygiene, and create a page only when durable content warrants it |
| `architectural-health-review` | Source access, documented/repository-discovered scope and writable review location | Evidence-backed six-area review; runtime/realtime questions are calibrated to actual systems; dated report, no automatic redesign or implementation |

## Validation resolution

Issue classification preserves the working resolution order: workstream
`Slice Validation.md`, repository-wide contributor validation, then an explicit
user-provided validation document. Record the selected document's path.
For implementation, ensure that contract is discoverable beside the issue plan
or through the repository-wide contributor reference. If only an external
user-provided contract exists, explicitly record it as the workstream contract
or link it from the contributor guidance before implementation. The
implementer preserves its two-source discovery gate rather than silently
substituting an undocumented process.

The starter's [Validation reference](../starter/Project%20Knowledge/contributor-references/Validation.md)
is a setup scaffold. An adopter must configure applicable commands, environment
requirements, and failure criteria before implementation. Copying the starter
does not make a project technically ready.

## Output and resume conventions

Planning artifacts normally share a named workstream folder. The durable
implementation report lives in the separately documented implementation-report
area and uses `YYYY-MM-DD <Workstream Name> Report.md`. Its date is the creation
date. Search for an existing report and resume it; multiple matching reports
require disambiguation. These are the skills' reporting conventions;
an adopter can document equivalent locations without weakening persistence,
uniqueness, traceability, or resumability.

Human acceptance pending at a non-blocking checkpoint does not claim completion
of that checkpoint. Preserve the handoff and continue only later AFK work
authorized by the plan. A failed technical check, blocking dependency, or
explicit stop-before point still stops execution.

## Optional metadata and interfaces

Three skill folders retain their original `agents/openai.yaml` metadata.
`architectural-health-review` retains `allow_implicit_invocation: true`.
These files provide optional Codex interface/policy settings and declare no
tool dependency. Other hosts can ignore them; use `SKILL.md` and its references
through that host's supported mechanism.

No editor configuration, plugin, board, card schema, remote service,
multi-agent backend, or product-specific release machinery is bundled or
required. Actual cross-host execution remains untested.
