# When To Use What

A decision framework for matching a tool/approach to a task. Two axes decide almost everything.

## The two axes

- **Input variation** — low (same shape every time) ⟷ high (unpredictable, open-ended)
- **Ease of verification** — easy (a clear, cheap check exists) ⟷ hard (correctness is subjective or expensive to confirm)

## The quadrants

| | Easy to verify | Hard to verify |
|---|---|---|
| **Low variation** | **Pipelines** — fixed steps, predictable inputs, the same checks every run | **Copilots** — repetitive but judgment-laden; AI assists, human stays in the loop |
| **High variation** | **Autonomous agents** — bounded variation around reliable, verifiable tools | **Human judgment + templates** — the machine drafts/scaffolds, the human decides |

## Examples placed on the grid

| Task | Quadrant |
|---|---|
| Routine assay analysis | Pipeline |
| Standard QC reports | Pipeline |
| Summarizing papers | Copilot |
| Reading & summarizing emails into a text to you | Autonomous agent (easy to verify) |
| Reading and responding to emails | Copilot / human-in-loop (harder to verify) |
| Designing a new analysis strategy or pipeline | Human judgment + templates |
| Interpreting surprising results | Human judgment + templates |
| Reviewing a manuscript | Human judgment + templates |

## The rule of thumb

> **Agents are useful when scientific work is variable but verifiable.**

- The easier it is to **verify**, the more autonomy you can safely grant.
- The higher the **variation**, the more an agent (vs. a fixed pipeline) earns its keep.
- When verification is hard, keep the human in the decision seat and use the agent to draft, scaffold, or triage — not to decide.

Pair this with the seven-box lens (`docs/seven-box-lens.md`): if the **Check** box is easy to fill in, you are toward the left of the grid and can lean more autonomous.

