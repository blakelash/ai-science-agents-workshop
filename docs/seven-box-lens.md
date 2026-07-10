# The Seven-Box Lens

The core mental model of the workshop. Ask these seven questions about **any** workflow before you decide whether — and how — to hand it to an agent.

| Box | Question |
|---|---|
| **Inputs** | What goes in? |
| **Agent needs** | What must it be able to do? |
| **Tools / access** | What can it touch? |
| **Artifact** | What appears at the end? |
| **Check** | How do we verify it? |
| **Escalation** | When does a human take over? |
| **Failure modes** | What does going wrong look like? |

## Why this lens

The thesis of the workshop is:

> **Agents are useful when scientific work is variable but verifiable.**

The seven-box lens operationalizes that. Most of the boxes exist to force the *verifiable* half into the open:

- **Artifact** makes the output inspectable.
- **Check** names how you confirm it.
- **Escalation** names the human handoff.
- **Failure modes** names what going wrong looks like *before* it happens.

A workflow you can fill in confidently is a workflow you can trust an agent with. A workflow where the Check/Escalation/Failure-mode boxes are vague is one that still needs a human in the loop.

## How to use it

1. Copy `templates/seven-box-template.md`.
2. Fill in one box at a time for your task.
3. If you cannot fill in **Check** and **Failure modes**, the task is not yet ready for autonomy — keep a human in the loop or add a verification step first.

## Worked examples

Every demo in this repo (`demo-1/` … `demo-5/`) is a filled-in seven-box card. Read them as concrete examples of the lens applied to real scientific tasks.

