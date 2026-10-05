# VibeFlow

**A structured vibe-coding workflow for non-traditional developers.**

If you already build software by talking to an AI, VibeFlow gives those
conversations structure so decisions and context survive beyond the chat.

## VibeFlow in plain English

You bring an idea and talk it through with your coding agent. The agent records
important decisions so they survive the conversation. When useful, those
decisions become requirements and manageable pieces of work. The agent builds
and technically checks the work, then updates the project's knowledge with
verified changes. You decide the product direction and whether the experience
is actually right.

You do not need to memorize artifact names, manage every handoff, become the
documentation administrator, or learn the complete operating specification
before beginning. Much of the structure is for the agent: preserving context,
resuming work, retaining evidence, and separating plans from implemented facts.

## How the work connects

**Explore → Define → Break down → Build and check → Remember**

| You want to… | VibeFlow uses… |
| --- | --- |
| Figure out what you actually want | [grill-me](skills/grill-me/SKILL.md) |
| Turn those decisions into clear requirements | [to-prd](skills/to-prd/SKILL.md) |
| Break the work into manageable pieces | [to-issues](skills/to-issues/SKILL.md) |
| Build and check those pieces | [implement-issues](skills/implement-issues/SKILL.md) |
| Keep the project's understanding current | Project Knowledge + [wiki-update](skills/wiki-update/SKILL.md), as appropriate |

For larger work, each step leaves behind useful context for the next, saving
you and your agent from reconstructing old conversations.
[architectural-health-review](skills/architectural-health-review/SKILL.md)
provides periodic technical-health review outside this chain.

Use the chain for substantial or ambiguous work. Small, clear changes can go
straight to implementation with enough context and appropriate checks, without
a PRD or issue plan.

`grill-me` welcomes rough ideas. Bring the relevant thinking you already
have—purpose, users, constraints, decisions, and uncertainties—and a useful
boundary, so it can challenge assumptions, expose gaps, and refine your idea
instead of discovering the basics.

Explore the whole product if useful; implement coherent features or pieces.
VibeFlow isn't a one-shot “build my entire app” pipeline. Build a piece,
evaluate it, learn, and continue.

## Your role and the agent's role

You decide product direction and whether the experience feels right. The agent
handles engineering within agreed scope and checks its work. Passing technical
checks does not mean you've accepted the experience.

**AFK** means work the agent can handle on its own; **HITL** (human-in-the-loop)
means it needs your decision, judgment, or review. The
[workflow guide](docs/workflow.md) explains precise meanings and
blocking/non-blocking behavior.

**Project Knowledge** gives the agent durable context. Reading and keeping it
current is part of the agent's work.

## Start here

Ready to try it? Give your coding agent the
[setup instructions](docs/agent-reference.md) and let it establish VibeFlow
for your project or idea. [Getting Started](docs/getting-started.md) provides
a request you can use—no need to configure everything yourself. The
[worked example](docs/example-workstream.md) is optional.

Use your preferred tools. Codex and Claude are examples of agents; Obsidian,
Kanban, GitHub, and other editors or trackers are optional interfaces.

## License and attribution

Matthew Gordon's original VibeFlow materials and additions are under the
[MIT License](LICENSE). Matt Pocock authored the original `grill-me`; Matthew
Gordon adapted it. Its [upstream MIT notice](skills/grill-me/LICENSE) and
[notice for Matthew Gordon's additions](skills/grill-me/VIBEFLOW-LICENSE) remain
with the skill. The other five skills are independently authored by Matthew
Gordon. See [attribution and license scope](docs/attribution.md).
