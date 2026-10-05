# Getting started

Begin with an existing project or a new idea. You do not need code or build
tooling to explore an idea and start planning.

## 1. Give the agent your project or idea

Provide the project location or describe your idea. Give your coding agent
access to VibeFlow and its [Agent setup and operating reference](agent-reference.md).
You can delegate setup with this request:

```text
Set up VibeFlow for this project or idea. Read the Agent setup and operating
reference, inspect the available context, and establish the appropriate skills,
maintained Project Knowledge, and validation guidance. Preserve useful existing
project conventions. Perform ordinary, reversible setup within the project
and host scope I have granted. Tell me about anything you genuinely need me
to decide.
```

## 2. Let the agent establish the environment

The agent makes the appropriate skills available, reuses or adapts your Project
Knowledge, or copies the
[Markdown starter](../starter/Project%20Knowledge/Project%20Knowledge%20Root.md).
It makes sure it can find and maintain that knowledge. You don't need to manage
the operational files yourself.

For an existing project, the agent identifies how it is built, tested, and
validated. For a new idea, you can begin exploring and planning immediately;
implementation and validation setup can come later. Before the agent starts
building, it must have an appropriate way to technically check its work.

Expect a short setup summary with any genuine blockers or decisions you need
to resolve.

## 3. Start work at the depth it needs

For something substantial or fuzzy, start with `grill-me`. Once you've figured
out what you want, the agent can turn that into requirements, break it into
manageable work, and implement it. See the
[worked example](example-workstream.md).

For something small and clear, just ask for the change. You don't need to run
the whole VibeFlow chain.

Technical checks don't replace your judgment about the resulting experience.
You decide whether it meets your intent and is ready to accept.

After setup, try:

```text
I have an idea for [describe the feature or problem]. Grill me.
```

Bring the relevant context and thinking you already have; a polished
specification isn't required. Keep the scope reasonably focused. The
conversation helps challenge, refine, and complete your idea.

Use your preferred agent, editor, and work-management tools. Codex, Claude,
Obsidian, Kanban, and GitHub are optional choices. The
[workflow guide](workflow.md) explains authority and AFK/HITL checkpoints.

[Back to VibeFlow](../README.md)
