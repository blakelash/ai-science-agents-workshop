# Demo 3 — Decompose + Traceable Analysis

**Surface:** Claude Science · *other options: Claude Code, Codex, Cursor, Kosmos, Biomni, K-Dense*

**New capability:** code execution (traceable analysis) + multi-agent task specialization.

## Goal

Break a paper's claims down and analyze them against public data: are there discrepancies or agreements? Produce a **traceable evidence memo** where every conclusion links back to a cell, figure, or dataset.

## Seven-box lens

| Box | Answer |
|---|---|
| **Inputs** — what goes in? | The paper + its data and code |
| **Agent needs** — what must it do? | Read paper, extract claims, analyze data, audit results, write report |
| **Tools / access** — what can it touch? | Code execution, public data |
| **Artifact** — what appears at the end? | A cited report + traceable analysis and code |
| **Check** — how do we verify it? | Conclusions trace to notebook cells and figures |
| **Escalation** — when does a human take over? | After the report is written (human reviews before trusting) |
| **Failure modes** — what does going wrong look like? | Convincing prose with no traceability |

## Subagents / specialists

This demo is well suited to a small team of specialists rather than one monolithic agent:

1. **Paper reader / claim extractor** → claim card
2. **Data analysis agent(s)** → notebook, plots, tables
3. **Auditor** → checks whether the analysis actually supports the claims
4. **Report writer** → synthesizes the traceable evidence memo

Connectors / MCPs supply the data and code access — use a tool with this built in, or wire it into the prompt.

## What is new here

This is where the workflow becomes about **specialization + verification**, not just "thinking harder." The provenance table — conclusion → evidence artifact → notebook source → confidence → caveat — is the point.

## Audience question

If an agent says the data support a paper's central conclusion, what would you want to inspect before trusting it?

