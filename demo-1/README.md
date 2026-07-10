# Demo 1 — Read

## Surface

Claude (chat / document reading).

## Scientific job

Take a single paper and turn it into a structured, slide-ready understanding a scientist can trust and reuse.

## Inputs

- `paper.pdf` — the anchor paper for the workshop

## What the system needs

- careful reading of one full paper
- separation of core claim from supporting detail
- honest handling of what the paper does *not* establish

## Suggested Claude prompt

> Read the attached paper and help me turn it into a workshop demo for scientific agents. Please do four things: (1) summarize the core claim in 5-7 bullets, (2) identify the specific steps that are deterministic pipeline components versus places where an agent or copilot could add judgment, (3) propose one bounded, realistic live demo based on this paper that could be reproduced in a workshop setting, and (4) list the validation checks and failure modes I should mention if I present this as an example of agentic science tooling. Keep the output practical and slide-ready.

## Artifact

A **paper brief** covering:
- core claim in 5–7 bullets
- deterministic pipeline steps vs. judgment steps
- one bounded, reproducible demo idea
- validation checks and failure modes

## Check / failure mode

- **Failure mode:** confident summary that misstates the claim or overstates certainty
- **Check:** every key claim should trace back to a specific figure, table, or passage in the paper

## Audience question

- When you read a new paper, what do you most want an agent to get *right* on the first pass?

## What is new here

This is the foundation of the arc: **read one paper well.**

Every later demo builds on this — you cannot contextualize, test, monitor, or remember what you never accurately read in the first place.

