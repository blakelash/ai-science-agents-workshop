# Demo 2 — Contextualize

**Surface:** Claude Cowork + Paperclip · *other options: NotebookLM, Elicit, PaperQA2 / Edison Lit*

**New capability:** tool use — content retrieval via an MCP server.

## Goal

Place the paper in its wider scientific context: novelty, related work, competition, and uncertainty.

## Seven-box lens

| Box | Answer |
|---|---|
| **Inputs** — what goes in? | The paper + literature retrieval |
| **Agent needs** — what must it do? | Search, compare, and cite related work |
| **Tools / access** — what can it touch? | Web + literature search |
| **Artifact** — what appears at the end? | A context memo with citations |
| **Check** — how do we verify it? | Citations resolve to real papers |
| **Escalation** — when does a human take over? | Before repeating any novelty claim |
| **Failure modes** — what does going wrong look like? | False novelty, invented context |

## What is new here

This is the jump from *"read this paper well"* to *"situate this paper in the field."* The point is not better summarization — it is that the paper alone is almost never enough context for scientific judgment. This is also the first demo where the agent uses a **tool** (retrieval via MCP) rather than just reasoning over what it was handed.

## Audience question

What outside context would most change your opinion of a new paper?

