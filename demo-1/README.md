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

> Read the attached paper carefully and help me understand it as a working scientist would. Please: (1) state the central claim in 5–7 bullets, (2) explain the key methods and what evidence actually supports the main result, (3) call out the most important limitations, caveats, or places the conclusions may outrun the data, and (4) list the open questions or follow-up experiments this paper raises. For every substantive claim, cite the specific figure, table, or section it comes from, and flag anything you are unsure about rather than guessing.

## Artifact

A **paper brief** covering:
- central claim in 5–7 bullets
- key methods and the evidence behind the main result
- important limitations and caveats
- open questions / follow-up experiments
- each claim tied to a specific figure, table, or section

## Check / failure mode

- **Failure mode:** confident summary that misstates the claim or overstates certainty
- **Check:** every key claim should trace back to a specific figure, table, or passage in the paper

## Audience question

- When you read a new paper, what do you most want an agent to get *right* on the first pass?

## What is new here

This is the foundation of the arc: **read one paper well.**

Every later demo builds on this — you cannot contextualize, test, monitor, or remember what you never accurately read in the first place.


