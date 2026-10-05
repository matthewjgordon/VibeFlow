---
name: wiki-update
description: Maintain the project's Markdown wiki as an architectural knowledge base by reviewing current implementation, implementation reports, related planning artifacts, and existing wiki pages; then updating durable concepts, ownership boundaries, rationale, constraints, preserved extensibility, cross-links, and navigation. Use when the user asks to update, refresh, reconcile, audit, or maintain the project wiki after implementation or architectural change.
---

# Wiki Update

Maintain the project's Markdown wiki as a durable architectural knowledge base.

The wiki exists to help a future contributor, AI agent, or project owner
understand why the system is built this way. Do not turn it into a comprehensive
code reference or a copy of project artifacts.

## Project Knowledge Discovery

At the repository root:

1. Inspect for `Project Knowledge/Project Knowledge Root.md`.
2. Read it when present. Begin within its documented knowledge area and treat
   it as the authoritative project-knowledge area.
3. Follow its links to the wiki, implementation reports, contributor
   references, architecture reviews, and active-workstream location.
4. If it is absent, inspect the repository documentation structure before
   choosing paths.

Do not assume a physical folder name for project artifacts. Use
repository-relative paths in wiki source landmarks.

## North Star

Optimize for answering:

> Why is the system built this way?

Do not optimize for answering:

> How can I reproduce every line of the implementation?

Capture enough durable context to explain:

- What a system does
- What responsibilities it owns
- What responsibilities it deliberately does not own
- How it relates to other systems
- Why important architectural decisions were made
- Which assumptions and invariants future contributors should preserve
- What future flexibility was intentionally preserved

## Source Hierarchy

When sources disagree, use this order:

1. Treat current source code as authoritative for current behavior.
2. Use implementation reports as the primary source of rationale.
3. Use existing wiki pages for continuity and established vocabulary.
4. Use architecture reviews and workstream plans as supporting context.
5. Use PRDs and issue breakdowns as intent only. Do not let them override the
   implementation.

Document what currently exists. Do not present abandoned, superseded, proposed,
or partially implemented designs as current architecture.

## Information Selection

Prefer durable architectural information:

- Ownership boundaries
- Responsibility allocation
- Relationships between systems
- Architectural decisions and their rationale
- Rejected abstractions when the rejection remains important
- Constraints, invariants, and deliberate limitations
- Preserved extension points and deferred capabilities
- Canonical state, derived state, and lifecycle boundaries
- Important product-policy boundaries

Avoid low-value detail:

- Individual methods
- Individual classes unless architecturally significant
- Mechanical implementation details
- Temporary workarounds
- Historical implementation steps
- Issue-by-issue history
- PRD summaries
- Exhaustive file lists
- Code-reference duplication

Use source landmarks sparingly to orient contributors toward significant
implementation boundaries.

## Markdown Navigation Conventions

Treat the wiki as a graph, not a tree.

- Use ordinary Markdown links: `[Page Name](Page%20Name.md)`.
- Use descriptive link text where it improves prose: `[display text](Page%20Name.md)`.
- Resolve relative paths from the linking file and follow the project's actual
  layout; pages need not live in a flat directory.
- Prefer meaningful conceptual page titles.
- Prefer conceptual navigation over folder hierarchy.
- Add links when they improve discoverability.
- Update related-page sections and overview navigation when concepts move.

### Link Philosophy

Links are cheap. Pages are expensive.

A concept reference does not automatically justify creating a page. It may
exist because the concept exists, is referenced by the architecture, or may
warrant documentation in the future. Use plain text for an unresolved concept
in ordinary Markdown; record it as a link-hygiene finding rather than creating
a dangling file link. Preserve its meaning and recommended disposition.

Create a page only when enough durable architectural knowledge exists to
justify ongoing maintenance. Do not create a page solely to resolve a missing
link.

### Link Hygiene

During maintenance, identify:

- Missing pages: referenced concepts without an existing note
- Stale links: links that no longer reflect the architecture or intended
  navigation
- Orphaned pages: existing notes without useful inbound navigation
- Navigation gaps: important concepts that are difficult to discover

Report findings. Recommend whether each finding should be created, merged,
deferred, removed, or otherwise reconciled.

Do not automatically create missing pages unless the concept clearly warrants
dedicated documentation. For example, report missing Contributor Guide or
Known Gaps And Future Work pages and recommend a disposition rather than
creating placeholder notes.

Ignore link-like text inside fenced code blocks and inline code when
auditing links. Examples and serialized data are not graph edges.

## Existing Wiki Shape

Preserve the current conceptual style unless the architecture warrants a
change. Existing pages commonly use:

- Introductory concept summary
- `Related Pages`
- Responsibility or ownership sections
- Relationships to adjacent systems
- `Why This Exists`
- `Extensibility Preserved`
- `Constraints`
- `Source Landmarks`

Use only the sections that help the page. Do not force empty boilerplate.

Prefer updating existing pages. Create a new page only when a new architectural
concept has no natural home and enough durable knowledge exists to maintain it.

## Workflow

### 1. Establish Scope

Identify the implementation or architectural change to document.

Inspect:

- Current git status and relevant diff, when available
- Relevant source files
- Associated active-workstream or promoted implementation report
- Related workstream plan, PRD, and issue breakdown when useful
- Architecture reviews when they materially clarify context
- Existing wiki pages and cross-links
- `Wiki Reconciliation` sections from planning artifacts and reports when
  available

Do not revert or overwrite unrelated user changes.

### 2. Reconstruct Current Architecture

Determine:

- What changed in the implemented system
- Which system owns the behavior now
- Which responsibilities moved, narrowed, or expanded
- Which boundaries remain intentionally unchanged
- Why the implementation took its current shape
- Which future capabilities remain possible
- Which earlier documented statements are now stale

Resolve ambiguity against current code. Use reports to recover rationale, not
to override implementation.

### 3. Decide Documentation Scope

For each durable finding:

1. Update an existing page when the concept already has a natural home.
2. Update overview pages when navigation or the system map changed.
3. Update the project's Glossary page when shared vocabulary changed.
4. Update the project's Design Guardrails page when a durable constraint, invariant, or
   extension boundary changed.
5. Create a new page only for a genuinely distinct architectural concept with
   enough durable content to maintain.
6. Leave mechanical implementation details in source code and reports.

Do not maximize page count. Maximize architectural understanding.

### 4. Edit The Wiki

Keep edits coherent across the graph:

- Describe current architecture in present tense.
- Explain ownership and non-ownership explicitly when it prevents confusion.
- Preserve the distinction between canonical state, derived state, transient
  runtime state, and presentation state.
- Add or repair cross-links where they improve discovery.
- Remove or revise statements invalidated by source changes.
- Keep rationale concise and durable.
- Avoid copying report prose wholesale.

### 5. Verify The Result

Review the changed pages together, not only as isolated files.

Check:

- Current source code supports the documented behavior.
- Reports support the captured rationale.
- New text does not present planned work as implemented.
- Related pages remain mutually consistent.
- New page titles are meaningful.
- Internal links use ordinary Markdown syntax and resolve to the intended files
  or headings. Deferred concepts remain visible as plain-text references with
  recorded dispositions.
- Missing pages, stale links, orphaned pages, and navigation gaps are reported.
- Link-like text inside code examples was not mistaken for a graph edge.
- No placeholder page was created merely to satisfy a link.

### 6. Report Maintenance Results

Summarize:

- Pages updated
- Pages created and why each warranted dedicated maintenance
- Durable architectural changes captured
- Link-hygiene findings and recommended dispositions
- Relevant implementation detail intentionally left out
- Any unresolved ambiguity or verification gap

## Success Criteria

A successful wiki update lets a future reader answer:

- What changed?
- Why did it change?
- Which system owns it?
- Which system does not own it?
- How does it relate to the rest of the architecture?
- Which constraints must future work preserve?
- What future flexibility remains intentional?

The reader should not need to reconstruct these answers from reports, PRDs,
issue breakdowns, or source history.

## Constraints

- Do not duplicate the codebase.
- Do not copy project artifacts into the wiki.
- Do not document unimplemented intent as current architecture.
- Do not create pages solely to remove unresolved wiki links.
- Do not erase unresolved concepts merely because the target page does not exist.
  Preserve the concept as plain text and report its disposition when replacing
  a dangling link.
- Do not silently ignore graph-hygiene findings.
- Do not perform unrelated code or documentation refactors.

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
