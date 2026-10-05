---
name: implement-issues
description: Implement a markdown issue plan, especially an Issues.md document produced by the to-issues skill, by completing each issue in sequence, validating each slice against the applicable workstream or contributor validation document before moving on, and maintaining a dated implementation report under the repository's Project Knowledge implementation-reports folder. Use when the user asks a coding agent to implement issues, work through an Issues.md file, execute a to-issues output, run unattended issue implementation, or continue issue-by-issue implementation from a markdown implementation plan.
---

# Implement Issues

Implement an `Issues.md` plan as a sequence of bounded vertical slices. Treat each issue as the unit of work, and do not advance to the next issue until the current issue is implemented, checked, and reconciled against the applicable validation document.

This skill focuses on:
- repository-aware implementation
- issue-by-issue execution
- slice validation before progression
- preserving the intent of the original issue plan
- reporting completed, blocked, skipped, and deferred work clearly in a dated implementation report under `Project Knowledge/implementation-reports/`

NOT:
- rewriting the issue plan unless the user asks
- batch-implementing multiple issues without validation checkpoints
- skipping acceptance criteria because tests pass
- treating `Issues.md` as advisory when it conflicts with explicit validation docs
- running indefinitely through ambiguous or interactive blockers

---

# Required Inputs

Work from an issue document supplied or referenced by the user. The issue document is usually named:
- `Issues.md`
- an Issues document in the repository's active-workstream area
- another markdown file explicitly identified by the user

Before implementing, locate and read:
- `Project Knowledge/Project Knowledge Root.md`, when the repository provides
  one; begin within its documented knowledge area and treat it as the
  authoritative project-knowledge area
- the referenced issue document
- `Slice Validation.md` in the same folder as the referenced issue document, if present
- otherwise the repository-wide contributor reference identified by the
  project-knowledge root or repository inspection
- the wiki home, design guardrails, and focused wiki pages identified by the
  issue document or project-knowledge root

If neither validation document exists, pause and tell the user. Do not silently substitute a weaker validation process unless the user explicitly approves it.

Create or update:
- the canonical implementation report in the repository's documented implementation-reports area, named `YYYY-MM-DD <Workstream Name> Report.md`

Use that dated implementation report as the durable implementation log for the run. Do not create or update `report.md` beside the issue document unless the user explicitly requests a temporary local report.

Do not assume a physical documentation folder name. Follow the repository's
documented knowledge conventions when they exist.

---

# Core Workflow

## 1. Preflight The Run

Before implementing the first issue, perform a preflight pass.

Check:
- the issue document exists and is readable
- the issue document's containing folder is readable
- the canonical implementation-reports folder is writable
- the applicable validation document exists and is readable
- the git worktree state, noting pre-existing user changes without reverting them
- required validation commands from the applicable validation document
- obvious missing tools, dependencies, credentials, simulators, services, or environment variables
- likely permission prompts, network access, package installs, GUI automation, or interactive commands
- issues that require blocking HITL approval, unresolved product judgment or design preferences, or acceptance criteria that cannot be resolved from evidence
- non-blocking human acceptance that can remain pending while later AFK work proceeds

If preflight finds a blocker that would prevent unattended execution, stop before editing code and report it clearly. If preflight finds non-blocking risks, record them in the run's implementation report and continue.

Do not use destructive commands during preflight. Do not install dependencies, change credentials, start paid external services, or mutate remote systems unless explicitly approved by the user.

## 2. Establish The Queue

Read the full issue document first.

Identify:
- the ordered list of issues or slices
- dependencies between issues
- acceptance criteria for each issue
- explicit non-goals or constraints
- any HITL items that require user judgment, including whether each is blocking

For a non-blocking HITL acceptance item, prepare the agreed evaluation handoff,
record human acceptance as pending, and continue the later AFK work authorized
by the plan. Do not perform the human's subjective evaluation or mark that item
accepted. Stop at blocking HITL, an explicit stop-before point, or a dependency
whose outcome determines subsequent implementation.

Preserve the issue order unless:
- dependencies require a different order
- the issue document explicitly allows reordering
- the user instructs otherwise

If the document has ambiguous issue boundaries, infer the smallest coherent implementation slices and state the interpretation before editing code.

## 3. Load Validation

Read the applicable validation document before starting the first issue.

Use it as the gate for every issue. Extract:
- required validation commands
- manual validation expectations
- review checklist items
- documentation or changelog requirements
- completion criteria
- any conditions that require stopping for user review

If validation instructions are broad, apply the subset relevant to the current issue and explain any skipped checks.

## 4. Resolve And Initialize The Report

Create or update the dated implementation report before editing implementation files.

Report path rules:
- Use the repository's documented implementation-reports area, for example `Project Knowledge/implementation-reports/`.
- Name the report `YYYY-MM-DD <Workstream Name> Report.md`.
- Derive `<Workstream Name>` from the active-workstream folder when the issue document lives under `active-workstreams/<Workstream Name>/`; otherwise derive it from the issue document title and stop if ambiguous.
- Before creating a new file, search the implementation-reports folder for an existing `????-??-?? <Workstream Name> Report.md`. If exactly one exists, update it. If none exists, create one using the current local date. If multiple exist, stop and ask which report to use.
- Treat issue-plan references to `active-workstreams/<Workstream Name>/report.md` as stale unless the user explicitly asks for a temporary local report.
- Do not create or update `report.md` beside the issue document by default.

The report must include:
- source issue document path
- applicable validation document path
- run start timestamp when available
- preflight summary
- issue queue with statuses
- per-issue implementation notes
- per-issue validation results
- skipped, blocked, deferred, or partially completed issues with reasons
- future concerns and follow-up recommendations
- wiki reconciliation handoff

Use these statuses:
- `pending`
- `in_progress`
- `implemented`
- `validated`
- `blocked`
- `skipped`
- `deferred`
- `partial`

Update the report after every issue validation checkpoint and whenever an issue is skipped, blocked, or deferred. The report should be useful even if the run is interrupted.

## 5. Implement One Issue At A Time

For each issue:

1. Restate the issue identifier or title being implemented.
2. Gather only the code context needed for that issue.
3. Implement the narrowest change that satisfies the issue and its acceptance criteria.
4. Avoid unrelated refactors, cleanup, formatting churn, or opportunistic fixes.
5. Run the validation required by the applicable validation document.
6. Compare the result against the issue acceptance criteria.
7. Fix any failures before moving on.
8. Update the run's implementation report with implementation status, validation results, changed files, and future concerns.

Do not start implementation work for the next issue until the current issue has passed its validation gate or is explicitly blocked.

## 6. Handle Blockers

If an issue cannot be completed:
- stop at the blocked issue
- preserve completed work from prior issues
- explain the blocker concretely
- include the file, command, missing decision, missing dependency, or failing check involved
- update the run's implementation report before stopping
- ask only the narrow question needed to unblock progress

Do not skip ahead to later issues unless the user explicitly approves continuing out of order.

If an issue is intentionally skipped:
- require an explicit reason from the issue document, validation document, or user
- record the skip reason in the run's implementation report
- continue only if skipping does not invalidate dependent issues

## 7. Maintain Status

For multi-issue work, keep a concise implementation queue visible in updates:
- `pending`
- `in_progress`
- `implemented`
- `validated`
- `blocked`
- `skipped`
- `deferred`

Update the user-facing status and the run's implementation report after each validation checkpoint. Keep the queue high signal; do not paste the entire issue document back to the user.

---

# Unattended Execution Policy

Optimize for the user being away from the computer, but do not guess through material uncertainty.

Continue without asking when:
- the issue acceptance criteria are clear
- validation commands are explicit and non-destructive
- failures are caused by the current issue and can be fixed in scope
- changes stay within the repository and expected writable paths
- broader validation is prudent because the issue touched shared behavior

Stop and ask when:
- unresolved product intent, UX or copy preferences, or architectural tradeoffs genuinely require human authority before dependent work can proceed
- validation requires credentials, private services, paid resources, or missing external access
- a command requires unapproved elevated permission and is necessary to continue
- a dependency install or network operation is required but not pre-approved
- an interactive command cannot be made non-interactive safely
- the worktree contains conflicting user changes in files that must be edited
- the next issue depends on a blocked, skipped, or failed issue
- implementation would require destructive git operations, data deletion, migrations against live systems, or remote mutation

When stopping, leave the run's implementation report current enough for the user or a later coding-agent run to resume.

---

# Validation Rules

Validation is issue-scoped first and repository-scoped second.

For each issue:
- run the smallest relevant checks from the applicable validation document
- run broader checks when the issue touches shared behavior, public interfaces, data migrations, build configuration, or cross-cutting architecture
- record any validation that could not be run and why

Passing tests alone is not sufficient if the issue acceptance criteria or validation document require additional technical inspection, generated artifacts, or documentation updates. Record human experiential/product acceptance separately. If it is explicitly non-blocking, its pending status does not prevent authorized later AFK work after the technical gate passes; blocking human gates still stop progression. Never label pending acceptance as complete.

When validation fails:
- inspect the failure
- fix the issue if it is in scope
- rerun the relevant check
- do not continue to the next issue with known failures unless the user explicitly accepts the residual risk
- record the failure and rerun result in the run's implementation report

---

# Report Format

Write the run's dated implementation report in concise markdown under the implementation-reports folder. Prefer this structure:

```markdown
# Implementation Report

## Sources
- Issues: path/to/Issues.md
- Validation: path/to/validation-document.md

## Preflight
- Status: completed | blocked
- Notes:

## Issue Summary
| Issue | Status | Validation | Notes |
| --- | --- | --- | --- |
| Issue title or ID | validated | passed | Short result |

## Issue Details

### Issue title or ID
- Status:
- Implemented:
- Files changed:
- Validation run:
- Validation result:
- Skipped/blocker reason:
- Future concerns:

## Outcome

## Implemented Scope

## Deferred Or Unimplemented Scope

## Architectural Decisions And Rationale

## Systems Changed

## Compatibility And Migration Notes

## Validation Evidence

## Known Limitations

## Wiki Reconciliation
- Wiki pages consulted:
- Existing guardrails relevant to this work:
- Planned architectural delta:
- Implemented architectural delta:
- Wiki pages likely requiring updates:
- Reconciliation required: Yes | No
- Reconciliation status: Not started | Completed | Not required
```

Keep the report factual. Do not hide failures or skipped work behind generic language.
The report should stand alone as durable project knowledge while active-workstream planning artifacts remain temporary.

---

# Implementation Discipline

Respect the repository's existing:
- architecture
- naming conventions
- testing patterns
- formatting tools
- domain terminology
- dependency boundaries

Prefer:
- vertical, observable progress
- small stable interfaces
- deep module changes over scattered utility code
- tests that verify behavior from the outside
- documentation updates when required by the issue or validation contract, or when verified changes make relevant durable project knowledge stale or contradictory

Avoid:
- broad rewrites
- premature abstraction
- hidden behavior changes outside the current issue
- modifying unrelated issue text or planning docs unless needed to record status
- collapsing multiple slices into one large implementation pass

---

# Final Response

When all requested issues are complete, summarize:
- issues completed
- files changed
- validation run
- validation not run, with reasons
- implementation report location
- wiki reconciliation status
- any remaining risks or follow-up issues

When stopped by a blocker, summarize:
- issues completed before the blocker
- the blocked issue
- the exact blocker
- implementation report location
- the narrow next decision or action needed

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
