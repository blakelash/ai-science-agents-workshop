# Demo 1 — Read

**Surface:** Claude (chat) · *other options: ChatGPT, Gemini, any strong chat model*

**New capability:** baseline — an LLM reading and reasoning over one document.

## Goal

Have an LLM read a new paper and summarize its findings into a structured, checkable readout a scientist can trust.

## Seven-box lens

| Box | Answer |
|---|---|
| **Inputs** — what goes in? | The paper + instructions on the output format |
| **Agent needs** — what must it do? | Read the paper, write text |
| **Tools / access** — what can it touch? | The paper (nothing else) |
| **Artifact** — what appears at the end? | A structured readout with citations to particular lines |
| **Check** — how do we verify it? | Every claim traces to a specific figure, table, or passage |
| **Escalation** — when does a human take over? | At the next turn (you review and redirect) |
| **Failure modes** — what does going wrong look like? | Overclaiming, misreading, fake-generic limitations |

## Suggested prompt

> Read the attached paper carefully and help me understand it as a working scientist would. Please: (1) state the central claim in 5–7 bullets, (2) explain the key methods and what evidence actually supports the main result, (3) call out the most important limitations, caveats, or places the conclusions may outrun the data, and (4) list the open questions or follow-up experiments this paper raises. For every substantive claim, cite the specific figure, table, or section it comes from, and flag anything you are unsure about rather than guessing.

## Files

- `paper.pdf` — the anchor paper used across the workshop

## What is new here

This is the foundation of the arc: **read one paper well.** Every later demo builds on it — you cannot contextualize, test, monitor, or remember what you never accurately read in the first place.

## Audience question

When you read a new paper, what do you most want an agent to get *right* on the first pass?

