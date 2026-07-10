# Demo 3 — Decompose + Traceable Data Analysis

## Surface

Claude Science, with Claude Code / Codex / Cursor as fallback implementation surfaces.

## Scientific job

Take a central claim from the anchor paper, operationalize it into a measurable question, run a notebook analysis, and produce a **traceable evidence memo** showing whether the available data support, weaken, or fail to address the claim.

## Inputs

- paper + context memo
- central claim to test
- accessible data / supplement / figure / table

## Subagents / specialists

- **Claim extractor** → claim card
- **Analysis planner** → analysis plan
- **DA agent** → notebook, plots, tables
- **Reviewer / auditor** → traceability audit
- **Synthesizer** → mini evidence memo

## What the system needs

- claim operationalization
- traceable notebook-based analysis
- review / audit layer that checks whether conclusions trace to outputs

## Tools / access needed

- analysis workspace / notebook
- code execution
- data or supplement access

## Artifact

- notebook
- plots / tables
- provenance / evidence table
- mini evidence memo

## Check / failure mode

- **Failure mode:** the DA agent sounds convincing, but the conclusion is not traceable to notebook cells, figures, tables, datasets, or assumptions
- **Check:** visibly show a provenance table linking:
  - conclusion
  - evidence artifact
  - notebook source
  - confidence
  - caveat

## Audience question

- If an agent says the data support a paper’s central conclusion, what would you want to inspect before trusting it?

## What is new here

This is where the workflow becomes about **specialization + verification**, not just “thinking harder.”

