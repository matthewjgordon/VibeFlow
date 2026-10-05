# Project Knowledge Root

This area holds maintained project knowledge: durable concepts, contributor
guidance, current planning, implementation evidence, reviews, and test results.
It is a recommended starter layout, not a mandatory hierarchy.

## Navigate

- [Wiki home](wiki/01%20Home.md) — concepts, vocabulary, rationale, and boundaries.
- [Contributor guide](contributor-references/Contributor%20Guide.md) — setup and working conventions.
- [Agent reference](contributor-references/Agent%20Reference.md) — discovery, decision authority, and knowledge upkeep.
- [Validation](contributor-references/Validation.md) — configure project-specific technical gates and human handoffs.
- [Active workstreams](active-workstreams/README.md) — intent and plans for current work.
- [Implementation reports](implementation-reports/README.md) — what changed, why, and how it was validated.
- [Architecture reviews](architecture-reviews/README.md) — dated observations and recommendations.
- [Test reports](test-reports/README.md) — procedures, results, evidence, and gaps.

## Maintained boundary

Register this root's actual path in project/agent instructions. Begin here when
project knowledge is relevant, then follow focused links. Material outside
the documented knowledge boundary is not automatically maintained knowledge;
an authoritative reference may point to useful source or external context.

The coding agent is responsible for consulting and maintaining relevant
knowledge. Verified changes must not leave stale or contradictory explanations
as misleading future context. Update facts and navigation, preserve useful
rationale, and report any unresolved reconciliation gap.

## Sources and authority

Human product decisions define intended behavior, preferences, and acceptance.
Current source code and verified runtime evidence establish implemented
behavior. Reports record changes, rationale, validation, and limitations.
The wiki explains durable concepts and should be reconciled against those
facts. Contributor references define current process and validation contracts.
Reviews capture a point in time; workstream plans describe intent.

A PRD or issue plan is not proof that a feature exists. Mark proposed,
implemented, superseded, deferred, and partially implemented information
clearly. Documentation does not initiate additional implementation.

## Lifecycle and storage

Planning → scoped implementation → durable report → knowledge reconciliation.
Keep these responsibilities distinct even if you choose a different hierarchy.
Retain, archive, or retire planning material deliberately according to project
needs; no deletion or archival policy is prescribed.

Version or back up durable knowledge. Choose whether it lives inside or outside
the application's Git repository, and provide the agent access to its actual
location. Ordinary Markdown files and folders are sufficient; no editor,
plugin, board, task-ID scheme, or metadata schema is required.
