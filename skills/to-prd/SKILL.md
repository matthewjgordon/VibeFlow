---
name: to-prd
description: Turn the current conversation context, feature discussion, or design exploration into a structured PRD suitable for implementation planning. Use when the user wants to formalize an idea, feature, workflow, or architectural concept into a PRD.
---

# To PRD

Turn the current conversation context and repository understanding into a structured Product Requirements Document (PRD).

This skill is intentionally:
- tooling-agnostic
- issue-tracker-agnostic
- LLM-agnostic

The PRD may later be:
- published to GitHub
- converted into Jira tasks
- transformed into Linear issues
- stored as markdown
- stored in Obsidian
- transformed into JSON/YAML
- or used by any implementation workflow

This skill focuses on:
- alignment
- synthesis
- architecture-aware planning
- implementation clarity
- reducing ambiguity
- enabling reliable issue decomposition

NOT:
- implementation
- code generation
- issue publishing
- autonomous execution
- repository mutation

---

# Core Philosophy

A PRD is NOT:
- a code specification
- an implementation script
- a layer-by-layer engineering plan
- exhaustive technical documentation

A PRD IS:
- a destination document
- a shared alignment artifact
- a structured representation of the current design understanding
- a bridge between ambiguity and implementation

The PRD should:
- preserve intent
- reduce ambiguity
- define expected outcomes
- clarify architectural direction
- create a stable foundation for issue decomposition

The PRD should NOT:
- overfit implementation details
- hardcode file paths
- tightly bind to current repository structure
- attempt to fully predict implementation

---

# Important Principles

- Alignment before implementation
- Clarity over verbosity
- Architecture awareness over implementation detail
- Deep modules over shallow module sprawl
- Interfaces over internals
- Behavior over file structures
- Stable concepts over transient implementation details
- Human judgment over blind automation

---

# Process

## Repository Knowledge Discovery

If repository context exists:
- inspect the repository for `Project Knowledge/Project Knowledge Root.md`
- read it when present
- begin within the root's documented knowledge area and treat it as the
  authoritative project-knowledge area
- follow its links to the wiki, contributor references, architecture reviews,
  and active-workstream location
- read the wiki home, design guardrails, glossary, and only focused wiki pages
  relevant to the feature
- use wiki terminology consistently

If no project-knowledge root exists, inspect repository documentation
conventions before choosing output paths. Do not assume a physical folder name.

## 1. Gather Context

Work from:
- the current conversation
- feature discussions
- architectural discussions
- brainstorming sessions
- design exploration
- existing PRDs
- repository context
- issue discussions
- prototypes
- research artifacts
- or any combination of the above

Do NOT unnecessarily re-interview the user if sufficient context already exists.

If critical ambiguity remains:
- ask targeted clarifying questions
- prefer one question at a time
- focus on ambiguity that materially affects implementation direction

---

## 2. Explore The Codebase (Optional)

If repository context is available:
- explore the current architecture
- identify relevant modules/services/systems
- identify terminology and domain vocabulary
- identify architectural patterns
- identify testing patterns
- identify existing abstractions

Respect:
- existing architecture
- naming conventions
- established terminology
- ADRs or architecture notes if present

---

## 3. Identify Major Architectural Areas

Before writing the PRD:
- identify the major systems involved
- identify likely integration points
- identify ownership boundaries
- identify candidate deep modules
- identify likely testing boundaries

Actively prefer:
- deep modules
- encapsulated complexity
- stable interfaces
- composable architecture

Avoid:
- shallow utility proliferation
- broad coupling
- implementation leakage
- premature technical detail

---

# Deep Module Guidance

A deep module:
- encapsulates significant internal complexity
- exposes a small stable interface
- is testable from the outside
- minimizes implementation leakage

Prefer architectural plans that:
- create or extend deep modules
- preserve clean boundaries
- improve testability
- reduce cognitive overhead

Avoid architectural plans that:
- spread behavior across many tiny modules
- require excessive orchestration
- tightly couple unrelated systems
- expose unnecessary internals

---

# 4. Validate Architectural Direction

Before finalizing the PRD:
- summarize the major architectural areas
- summarize candidate modules/systems
- summarize testing boundaries

Check whether:
- the architectural direction matches the user's expectations
- the implementation scope feels correct
- the abstraction boundaries feel reasonable
- there are concerns around coupling or complexity

If repository context exists:
- align proposed architecture with existing patterns where reasonable

---

# 5. Define Implementation Readiness

Before writing the final PRD, classify what is ready for downstream issue decomposition and what still needs human judgment.

Identify:
- decisions that are settled enough for implementation planning
- open questions that block implementation
- open questions that do not block implementation
- HITL gates that should stop autonomous implementation
- validation expectations that downstream issues must preserve
- the likely unattended implementation scope, if any

Do not hide material ambiguity in `Further Notes`. If an open question affects behavior, UX, architecture, data, validation, or operational risk, classify it in `Implementation Readiness`.

If there are unresolved questions that would prevent safe issue decomposition, ask targeted clarifying questions before finalizing the PRD, unless the user explicitly wants a draft with blockers called out.

---

# 6. Write The PRD

Use the template below.

The PRD should:
- synthesize the current understanding
- preserve intent
- clarify behavior
- define scope
- create implementation alignment
- create clear source material for `to-issues`

Avoid:
- excessive technical minutiae
- implementation scripts
- stale file references
- speculative implementation detail

Include the template's `Wiki Reconciliation` section so downstream planning
and wiki maintenance can distinguish planned intent from implemented reality.

---

# PRD Template

Read [references/prd-template.md](references/prd-template.md) before writing the PRD.

---

# Output Guidance

The default output should be saved as a markdown file in the same folder as the upstream artifact it references.

Prefer this convention:
- If the PRD is based on a `grill-me` artifact, save the PRD next to that artifact.
- If the upstream artifact lives in an active-workstream folder, save the PRD
  in that folder.
- If there is no upstream artifact path, save the PRD in the repository's
  documented active-workstream area.
- If the feature/workstream does not yet have a folder, ask the user for a name
  and create one under the active-workstream area.

If the repository's active-workstream location has not been established, or if
the correct location is ambiguous, seek clarification from the user before
writing the file.

When writing the PRD, include enough source-path context for `to-issues` to locate the PRD's folder and save later artifacts there.

The resulting PRD should:
- be implementation-oriented
- remain architecture-aware
- stay understandable by humans
- work well as source material for issue decomposition
- support later vertical-slice planning

The PRD should NOT:
- attempt to fully automate implementation
- over-specify technical details
- replace engineering judgment
- become a giant design document

---

## Evidence And Decision Authority

Resolve questions autonomously when repository inspection, maintained project
knowledge, documentation, tests, engineering reasoning, or established
conventions can answer them. Escalate unresolved product intent, preferences,
subjective experience, or tradeoffs that genuinely require human authority.
Technical uncertainty alone is not a reason to require human judgment.

Keep technical validation separate from human product acceptance. Report
pending human acceptance explicitly; passing technical checks does not imply
it. Consult relevant durable knowledge and update it when verified changes
make it stale or contradictory. Record proposed changes as intent and carry
unimplemented documentation changes into the reconciliation handoff.

The named knowledge root, wiki pages, and output folders in this skill are
discovery conventions. Follow documented adopter equivalents when provided;
do not require this exact hierarchy or filename. Preserve the responsibilities,
validation gates, writable outputs, and source-of-truth boundaries.
