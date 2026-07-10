# Agent Workshop

Scaffold repo for the scientific agents workshop.

## Repo structure

```text
agent-workshop/
├── README.md
├── slides/
├── demo-1/
│   └── paper.pdf
├── demo-2/
├── demo-3/
├── demo-4/
│   └── lit-radar/   # submodule -> literature-radar-skills
└── demo-5/
```

## Slides

Put deck files in `slides/`.

## Canonical demo arc

Aligned to the Notion workshop outlines:

1. **Demo 1 — Read**
2. **Demo 2 — Contextualize**
3. **Demo 3 — Decompose + Traceable Data Analysis**
4. **Demo 4 — Monitor / Reusable Routine**
5. **Demo 5 — Adapt with Memory**

Narrative spine:

> **Read → Contextualize → Decompose → Monitor → Adapt**
>
> Or in words: **from reading one paper to building a persistent research collaborator**.

## Demos

### Demo 1 — Read

Files:
- `demo-1/paper.pdf`

Suggested Claude prompt:

> Read the attached paper and help me turn it into a workshop demo for scientific agents. Please do four things: (1) summarize the core claim in 5-7 bullets, (2) identify the specific steps that are deterministic pipeline components versus places where an agent or copilot could add judgment, (3) propose one bounded, realistic live demo based on this paper that could be reproduced in a workshop setting, and (4) list the validation checks and failure modes I should mention if I present this as an example of agentic science tooling. Keep the output practical and slide-ready.

### Demo 2 — Contextualize

Take the same paper and place it in the broader field with retrieval-grounded context: novelty, related work, competition, and uncertainty.

### Demo 3 — Decompose + Traceable Data Analysis

Operationalize one central claim into a measurable question, run a notebook analysis, and produce a traceable evidence memo that links conclusions back to figures, tables, notebook cells, datasets, and assumptions.

### Demo 4 — Monitor / Reusable Routine

Package the literature-radar workflow into a reusable routine/repo with sources, scoring rubric, dedupe logic, and digest outputs.

Implementation repo used here:
- `demo-4/lit-radar/` → `blakelash/literature-radar-skills`

### Demo 5 — Adapt with Memory

Turn the reusable routine into a persistent collaborator by remembering feedback, preferences, exclusions, and what the user has found interesting before.


