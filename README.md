# AI Agents in Science Workshop

A hands-on companion repo for the **AI Agents in Science** workshop.

It walks through a single narrative: **from reading one paper to building a persistent research collaborator.** Each demo is a self-contained step with its own README, artifact, and discussion prompt.

## The narrative spine

> **Read → Contextualize → Decompose → Monitor → Adapt**

| # | Demo | Question it answers |
|---|------|---------------------|
| 1 | **Read** | Can an agent genuinely *understand* one paper? |
| 2 | **Contextualize** | Can it situate that paper in the wider field? |
| 3 | **Decompose + Traceable Data Analysis** | Can it test a claim with analysis you can *trust*? |
| 4 | **Monitor / Reusable Routine** | Can it become a repeatable, inspectable workflow? |
| 5 | **Adapt with Memory** | Can it become a collaborator that *remembers*? |

Each step adds one new capability the previous step lacked — the arc matters more than any single tool.

## Repo structure

```text
ai-agents-in-science-workshop/
├── README.md
├── slides/                     # deck files
├── docs/                       # the mental models behind the talk
│   ├── seven-box-lens.md       # the core lens for any workflow
│   ├── when-to-use-what.md     # variation × verifiability decision grid
│   ├── glossary.md             # shared vocabulary
│   └── trustworthy-agents.md   # what the demos had in common
├── templates/
│   └── seven-box-template.md   # fill-in template for your own task
├── demo-1/                     # Read
│   ├── README.md
│   └── paper.pdf
├── demo-2/                     # Contextualize
│   └── README.md
├── demo-3/                     # Decompose + Traceable Data Analysis
│   └── README.md
├── demo-4/                     # Monitor / Reusable Routine
│   ├── README.md
│   └── lit-radar/              # submodule -> literature-radar-skills
└── demo-5/                     # Adapt with Memory
    └── README.md
```

## How to use this repo

1. Read the two core mental models first: the **[seven-box lens](docs/seven-box-lens.md)** and the **[when-to-use-what grid](docs/when-to-use-what.md)**.
2. Work through `demo-1/` … `demo-5/` in order — each is a filled-in seven-box card for a real scientific task.
3. Use **[templates/seven-box-template.md](templates/seven-box-template.md)** to sketch one workflow from your own work.
4. The slides in `slides/` follow the same arc.

## Core idea

> **Agents are useful when scientific work is variable but verifiable.**

The demos are trustworthy for one reason: they can be *checked*. See **[docs/trustworthy-agents.md](docs/trustworthy-agents.md)**.

## Demos at a glance

- **[Demo 1 — Read](demo-1/README.md):** turn one paper into a structured, slide-ready understanding.
- **[Demo 2 — Contextualize](demo-2/README.md):** place the paper in the field with retrieval-grounded context.
- **[Demo 3 — Decompose + Traceable Data Analysis](demo-3/README.md):** operationalize a claim and produce a traceable evidence memo.
- **[Demo 4 — Monitor / Reusable Routine](demo-4/README.md):** package the literature-radar workflow into a reusable routine (`demo-4/lit-radar/` → `literature-radar-skills`).
- **[Demo 5 — Adapt with Memory](demo-5/README.md):** turn the routine into a persistent collaborator that learns from feedback.


