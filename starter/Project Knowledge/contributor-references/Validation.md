# Validation

**Setup required:** this starter is not yet a configured implementation gate.
The adopter must supply the applicable commands, environments, and failure
criteria below before implementation uses this reference. Do not execute
invented commands, treat the empty setup as a pass, or silently weaken the gate.

## Configure the project contract

| Check | Exact command or procedure | Environment/prerequisites | Passing evidence |
| --- | --- | --- | --- |
| Build/type check, when applicable | Not configured | Not configured | Not configured |
| Focused unit/component checks | Not configured | Not configured | Not configured |
| Relevant integration/acceptance checks | Not configured | Not configured | Not configured |
| Documentation/link checks | Not configured | Not configured | Not configured |
| Broader regression triggers | Not configured | Not configured | Not configured |

For each row, configure a real check or explicitly mark it not applicable with
a reason. Identify working directories, required tools/services, data/fixtures,
and non-destructive invocation. Inspect repository tooling before asking the
human for information that the project already establishes. Genuine unknown
requirements must be resolved before dependent execution.

## Workstream-specific validation

An active workstream may provide `Slice Validation.md` beside its issue plan.
Record the applicable contract path in the plan and implementation report.
Use this repository-wide reference when no workstream contract exists. The
chosen contract must provide explicit relevant checks and failure gates.

## Technical slice gate

Before the next implementation slice:

- Implement the scoped acceptance criteria and preserve applicable guardrails.
- Run the smallest relevant configured checks and fix in-scope failures.
- Broaden validation when shared behavior, public interfaces, migrations,
  build configuration, or focused failures justify it.
- Review affected durable knowledge and reconcile verified changes.
- Update the resumable report with implementation, results, evidence,
  limitations, and the separate human-evaluation status.

Stop on a failed required technical gate, missing indispensable tooling or
validation guidance, conflicting user changes, unauthorized operations, or an
unresolved decision that determines dependent implementation. Record the exact
blocker and the narrow next action. Do not mark failures as skipped success.

## Human experiential/product acceptance

Configure how the human evaluates observable behavior, usability, appearance,
and intended product value. Each planned human checkpoint should say whether
it is blocking and why its outcome matters at that point.

Prepare a concrete evaluation handoff: what is ready, how to access it, what
the human should evaluate, and known technical limitations. Report acceptance
as pending until the human provides it. Silence is not acceptance.

Non-blocking evaluation may remain pending while later authorized AFK work
continues. Stop before dependent work when human feedback determines what to
build next or the plan specifies a blocking checkpoint. Passing automated
checks never substitutes for subjective product acceptance.
