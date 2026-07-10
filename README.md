# Agent Workshop

Scaffold repo for the agent workshop.

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
│   └── lit-radar/   # nested git repo
└── demo-5/
```

## Slides

Put deck files in `slides/`.

## Demos

### Demo 1 — paper + Claude prompt

Files:
- `demo-1/paper.pdf`

Suggested Claude prompt:

> Read the attached paper and help me turn it into a workshop demo for scientific agents. Please do four things: (1) summarize the core claim in 5-7 bullets, (2) identify the specific steps that are deterministic pipeline components versus places where an agent or copilot could add judgment, (3) propose one bounded, realistic live demo based on this paper that could be reproduced in a workshop setting, and (4) list the validation checks and failure modes I should mention if I present this as an example of agentic science tooling. Keep the output practical and slide-ready.

### Demo 2 — exploratory copilot

A lightweight reconnaissance demo: point the model at a paper, dataset, website, or repo and ask it to inspect the material, identify what matters, and suggest next steps.

### Demo 3 — bounded agent

A more agentic demo: give the system a clear task, a small tool budget, and explicit validation criteria, then let it execute a short multi-step workflow and return a memo.

### Demo 4 — literature radar

`demo-4/lit-radar/` is a nested git repo for the literature radar demo: signal arrives, papers are triaged, interesting leads are escalated, and outputs are packaged into something a scientist can actually review.

### Demo 5 — review, critique, and escalation

A closing demo focused on judgment: have the system critique its own output, identify uncertainty, and cleanly hand decisions back to the human.

