# Knowledge conventions

Project knowledge must help a future contributor, agent, or owner understand
what exists, why it exists, which boundaries matter, and what remains unsettled.
The agent has an active responsibility to consult and maintain that context.

## Keep the kinds of evidence distinct

| Kind | How to read it |
| --- | --- |
| Product intent or agreed decision | Human-authorized direction; not proof of implementation |
| Current implementation | Supported by source or verified runtime evidence |
| Implementation report | What changed, rationale, validation results, and limits |
| Architectural principle or constraint | A durable boundary with rationale and a clear scope |
| Point-in-time review | An assessment of the inspected system, not an automatic work authorization |
| Open question | An unresolved choice or evidence gap, explicitly classified |
| Deferred direction | Preserved possibility outside the current implementation commitment |
| Superseded information | Historical context identified so it cannot silently override current facts |

## Reconcile rather than accumulate

When implementation changes, update existing conceptual explanations and
navigation. Preserve important rationale and deliberately retained extension
points, but revise claims that the source no longer supports. Explain any
unresolved discrepancy rather than guessing through missing evidence.

Keep mechanical code detail in source and test/report evidence. Keep current
process commands in contributor references. Keep workstream intent in its
planning artifacts. A concept page can link to those sources without copying
their complete contents.

## Navigation and page scope

Treat concepts as a graph even when files are organized into folders. Use
ordinary relative Markdown links and meaningful titles. Create a page when
enough durable understanding exists to justify maintenance. An unresolved
concept does not require an empty page or a dangling file link.

Identify missing concepts, stale links, orphaned pages, and navigation gaps.
Record whether a finding should be documented, merged, deferred, removed, or
otherwise reconciled. Preserve the meaning of unresolved concepts while
repairing broken navigation.

[Back to wiki home](01%20Home.md)
