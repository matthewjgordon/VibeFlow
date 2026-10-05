# Contributor Guide

Begin with the [knowledge root](../Project%20Knowledge%20Root.md). Read only
focused knowledge relevant to the work, plus the applicable process and
validation references. Current source remains authoritative for implemented
behavior; human authority governs product intent and acceptance.

## Set up this starter

1. Copy the folder to your chosen knowledge location and register the root
   path in the coding agent's project instructions.
2. Configure [Validation](Validation.md) with the project's actual commands,
   environments, failure gates, and human-evaluation expectations. This is
   required before using it as an implementation contract.
3. Confirm the agent can read relevant source and write the agreed workstream,
   implementation-report, review, and evidence locations.
4. Add durable project concepts to the [wiki](../wiki/01%20Home.md) as real
   decisions and implemented systems emerge. Add glossary or design-guardrail
   pages only when there is meaningful content to maintain.
5. Choose knowledge versioning/backup and a way to identify superseded plans
   or findings. Keep navigation and links current when changing this layout.

No command, product requirement, architecture fact, or human acceptance is
preconfigured or inferred by copying these files.

## Artifact organization

| Area | Responsibility |
| --- | --- |
| Wiki | Durable concepts, vocabulary, ownership, rationale, constraints, and preserved flexibility |
| Contributor references | Current engineering process, tooling, and validation guidance |
| Active workstreams | Decision artifacts, PRDs, issue plans, and work-specific validation intent |
| Implementation reports | Implemented outcome, rationale, validation evidence, gaps, and reconciliation |
| Architecture reviews | Point-in-time technical assessment and bounded recommendations |
| Test reports | Test context, procedures, actual results, logs, and limitations |

Use readable names. A workstream folder can hold its initial decision artifact,
PRD, issue breakdown, and optional `Slice Validation.md`. Create only the
artifacts the work needs.

Use `YYYY-MM-DD <Workstream Name> Report.md` in the implementation-report area.
The date is first creation; continue that report when the same workstream
resumes. An architecture review uses a dated descriptive filename. Equivalent
documented paths are acceptable; preserve traceability and a unique resumable
report rather than silently scattering the evidence.

## Human and agent responsibilities

Follow the [agent reference](Agent%20Reference.md). Resolve technical questions
through project evidence before escalating. The human evaluates product intent,
preferences, experience, and acceptance. Record technical outcomes and human
acceptance separately; a board state or test pass does not imply acceptance.

## Navigation and stewardship

Use relative Markdown links with descriptive text. Follow the actual folder
layout; encode spaces in link destinations. Verify links after moving or
renaming documents, update the relevant index, and distinguish unresolved
concepts from broken file links.

Knowledge maintenance is active engineering work: reconcile verified changes
and important rationale into the wiki, update process guidance when it changes,
and preserve honest report/test evidence. Do not copy every implementation
detail or planning step into durable concept pages.
