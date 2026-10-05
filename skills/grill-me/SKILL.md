---
name: grill-me
description: Stress-test a feature, architecture, workflow, or implementation plan through structured iterative questioning until a shared understanding is reached. Use when the user wants to refine an idea, reduce ambiguity, validate assumptions, or mentions "grill me".
---

# Grill Me

Relentlessly interrogate the current idea, feature, architecture, workflow, or implementation concept until a strong shared understanding is reached.

This skill is intentionally:
- tooling-agnostic
- workflow-agnostic
- issue-tracker-agnostic
- LLM-agnostic

This skill focuses on:
- alignment
- ambiguity reduction
- architectural clarity
- assumption discovery
- dependency discovery
- implementation readiness
- identifying hidden complexity
- creating a durable decision artifact for downstream skills

NOT:
- implementation
- autonomous planning
- issue creation
- code generation
- speculative overengineering

---

# Core Philosophy

The purpose of this skill is NOT to immediately generate:
- a plan
- a PRD
- a task list
- implementation code

The purpose is to:
- create alignment
- discover ambiguity
- expose hidden assumptions
- clarify constraints
- refine architectural direction
- reduce downstream implementation confusion

A successful grilling session produces:
- a shared design understanding
- clarified tradeoffs
- explicit decisions
- identified unknowns
- implementation-ready context
- a named markdown artifact in the repository's active-workstream area that
  later planning and implementation skills can use

The resulting conversation should be distilled into a durable artifact, not left only in chat history.

---

# Important Principles

- Alignment before implementation
- Questions before solutions
- Clarify ambiguity early
- Reduce hidden assumptions
- Explore constraints before planning
- Architecture matters
- Interfaces matter
- Feedback loops matter
- Human judgment matters

Avoid:
- rushing into implementation
- premature planning
- over-specifying solutions
- generating giant plans too early
- assuming missing information

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
- read the wiki home, design guardrails, glossary, and only the focused wiki
  pages relevant to the discussion
- use established terminology and surface conflicts with existing guardrails

If no project-knowledge root exists, inspect repository documentation
conventions before choosing artifact paths. Do not assume a physical folder
name.

## 1. Gather Existing Context

Work from:
- the current conversation
- repository context
- design discussions
- brainstorming
- feature requests
- architecture notes
- prototypes
- PRDs
- issue discussions
- or any combination of the above

Do NOT ask questions already answered in available context.

If repository access exists:
- explore the codebase before asking questions that code inspection can answer

Prefer:
- discovering answers through inspection
- reducing unnecessary user burden
- grounding questions in actual architecture

---

## 2. Identify Ambiguity

Actively search for:
- hidden assumptions
- unresolved constraints
- unclear ownership
- missing workflows
- undefined edge cases
- integration uncertainty
- operational uncertainty
- architectural ambiguity
- testing ambiguity
- unclear success criteria

Look for:
- places where implementation direction could diverge
- decisions with downstream consequences
- terminology inconsistencies
- implied but unstated requirements

---

## 3. Interrogate The Design

Interview the user relentlessly.

Walk through:
- each branch of the decision tree
- each dependency chain
- each architectural assumption
- each workflow path

Questions should:
- build on previous answers
- progressively refine understanding
- narrow ambiguity
- expose tradeoffs
- clarify intent

Avoid:
- shotgun-question lists
- overwhelming the user
- asking disconnected questions
- asking questions without purpose

---

# Questioning Rules

## Ask One Question At A Time

Always ask:
- one focused question
- with clear context
- with clear reasoning

Do NOT:
- dump large questionnaires
- ask unrelated questions simultaneously

---

## Provide Guidance

For each question:
- explain why the question matters if helpful
- provide recommended options where appropriate
- identify likely tradeoffs
- help the user reason through ambiguity

Do NOT remain passive.

Actively assist:
- architectural thinking
- implementation thinking
- tradeoff analysis
- simplification

---

## Prefer Decision Compression

When possible:
- narrow choices
- identify likely defaults
- propose sensible constraints
- reduce unnecessary complexity

Avoid:
- infinite-option brainstorming
- speculative overengineering
- complexity without justification

---

# Architectural Guidance

When relevant:
- identify likely module boundaries
- identify ownership concerns
- identify integration paths
- identify testing boundaries
- identify feedback-loop requirements

Actively look for:
- opportunities for deep modules
- stable interfaces
- isolated complexity
- composable architecture

Avoid:
- shallow module sprawl
- broad coupling
- hidden dependencies
- implementation leakage

---

# Testing And Feedback Loops

Actively explore:
- how success will be verified
- how behavior will be tested
- where feedback loops exist
- where integration risk exists

Strong feedback loops are important for:
- reliable implementation
- reliable autonomous work
- reducing debugging complexity
- maintaining architectural clarity

---

# Scope Management

Actively identify:
- what belongs in scope
- what should remain out of scope
- future enhancements
- speculative ideas
- implementation phases

Prevent:
- feature creep
- uncontrolled expansion
- ambiguous boundaries

---

# Repository Awareness

If repository context exists:
- align questions to the existing architecture
- use existing terminology
- respect existing patterns
- identify reusable systems
- avoid unnecessary rewrites

If the codebase appears problematic:
- identify architectural friction
- identify shallow-module sprawl
- identify weak testing boundaries
- identify integration risks

Do NOT immediately recommend large rewrites.

Prefer:
- incremental improvement
- isolated architectural strengthening
- clearer interfaces
- better boundaries

---

# Desired End State

The grilling session should eventually produce:

- clarified goals
- clarified constraints
- clarified workflows
- clarified architecture
- clarified integration points
- clarified success criteria
- clarified scope
- clarified tradeoffs
- a named documentation folder for the slice/workstream
- applicable wiki guardrails and any intentional architectural departure
- a markdown artifact containing locked questions, answers, and decisions

The conversation should feel:
- focused
- iterative
- collaborative
- architecture-aware
- implementation-aware

NOT:
- adversarial
- chaotic
- overly abstract
- prematurely implementation-heavy

---

# Artifact Creation

When the grilling session reaches a stable set of locked decisions, create a durable markdown artifact.

Before creating the artifact, prompt the user for a name for the slice/workstream. Suggest one or two names based on the conversation.

Example prompt:

`What should we name this slice/workstream? Suggested names: "Project Navigation Cleanup" or "Search Workflow". I will create a folder under the repository's active-workstream area and downstream artifacts can live in that same folder.`

If the user already provided a clear name, confirm the inferred name briefly before creating the artifact.

Create:
- a new folder under the repository's documented active-workstream area using
  the chosen name
- a markdown file inside that folder using the same name

Example:

```text
<active-workstreams>/Project Navigation Cleanup/Project Navigation Cleanup.md
```

Use the user's chosen display name for headings. Use a filesystem-safe version only when needed for the folder and file path. Preserve readability; do not over-normalize to opaque slugs unless the repository already uses that convention.

If the active-workstream location is not established or is ambiguous, ask the
user before writing.

The artifact should include:
- title
- source context summary
- locked questions and answers
- locked decisions
- constraints
- scope
- out of scope
- architecture notes
- validation and feedback-loop notes
- open questions that remain
- risks and concerns
- wiki reconciliation handoff
- recommended next artifact, such as PRD or issue breakdown
- artifact folder note explaining that future PRD, Issues, and Slice Validation files should be saved in this same folder, while the durable implementation report belongs in the documented implementation-reports area

Use concise markdown. Prefer factual, implementation-useful records over transcript-style chat logs.

Suggested structure:

```markdown
# <Slice / Workstream Name>

## Source Context

## Locked Questions And Answers

## Locked Decisions

## Constraints

## Scope

## Out Of Scope

## Architecture Notes

## Validation And Feedback Loops

## Open Questions

## Risks And Concerns

## Wiki Reconciliation
- Wiki pages consulted:
- Existing guardrails relevant to this work:
- Planned architectural delta:
- Implemented architectural delta: Not implemented by this artifact.
- Wiki pages likely requiring updates:
- Reconciliation required: Yes | No
- Reconciliation status: Not started | Not required

## Downstream Artifacts
- Folder: <active-workstreams>/<name>/
- Recommended next artifact:
- Future planning and slice-validation artifacts should be saved in this folder.
- Durable implementation report: the documented implementation-reports area.
```

Do not automatically create a PRD, issue document, or implementation plan unless the user asks. The grill-me artifact is the handoff material for those later skills.

---

# Transition Guidance

Once ambiguity is sufficiently reduced:
- the resulting context may be suitable for:
  - PRD generation
  - issue decomposition
  - architectural planning
  - implementation planning
  - prototype work

Do NOT automatically transition unless requested.

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

## Attribution

Adapted by Matthew Gordon from Matt Pocock's original `grill-me` skill.
See [ATTRIBUTION.md](ATTRIBUTION.md) for the verified upstream source and
[LICENSE](LICENSE) for the upstream MIT notice, which must accompany retained
upstream material. Matthew Gordon's additions are also MIT-licensed; see
[VIBEFLOW-LICENSE](VIBEFLOW-LICENSE). Preserve both notices with this adaptation.
