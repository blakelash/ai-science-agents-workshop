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

## Subagents — a primer

A **subagent** is a specialized agent the main agent delegates a task to. It runs in its **own context window**, does its job, and returns only a summary to the parent. That gives you three things that matter for scientific work:

- **Context isolation** — noisy intermediate output (logs, search results, big tables) stays in the subagent, so the main thread stays focused on decisions.
- **Specialization** — each subagent gets a narrow prompt, its own tool access, and sometimes its own model tuned for its job.
- **Separation of duties** — the agent that *does* the analysis is not the same one that *audits* it. That independence is what makes the check meaningful (see Demo 3's failure mode).

### When subagents are useful

- The task splits into **parallel, independent** pieces (explore several datasets at once).
- A step produces **verbose output** you won't reference again (a big data pull, a repo scan).
- You want an **independent reviewer** — an auditor that didn't write the code checking whether conclusions trace to evidence.
- You keep spawning the **same kind of worker** with the same instructions — encode it once.

Trade-off: subagents use more tokens than a single-agent run, because each does its own model + tool work. Reach for them when isolation, parallelism, or independent review is worth that cost — not by default.

### How you define one

Across the major platforms the pattern is nearly identical: a small file (usually Markdown + YAML frontmatter, or TOML) with a **name**, a **description** (when to delegate to it), an optional **tools** allowlist and **model**, and a **system prompt** body. Project-scoped files apply to one repo; user-scoped files apply everywhere. Example shape:

```markdown
---
name: analysis-auditor
description: Checks whether an analysis's conclusions trace to notebook cells, figures, and data. Use after any data-analysis step.
tools: [Read, Bash]
model: inherit
---
You are a skeptical reviewer. For each conclusion, find the exact cell,
figure, table, or dataset that supports it. Flag anything that does not
trace to a concrete artifact, and anything where the prose overstates the
evidence.
```

### Basically every coding-capable platform supports this now

Subagents (custom, specialized, delegated) are a standard feature across today's agent platforms — often with **cross-compatible file layouts**:

- **Claude Code** — `.claude/agents/` (project) or `~/.claude/agents/` (user); Markdown + YAML frontmatter. Docs: https://code.claude.com/docs/en/sub-agents
- **Cursor** — `.cursor/agents/` (also reads `.claude/agents/` and `.codex/agents/` for compatibility). Docs: https://cursor.com/docs/subagents
- **OpenAI Codex** — `.codex/agents/` (project) or `~/.codex/agents/` (user); TOML. Docs: https://developers.openai.com/codex/subagents

The takeaway for the workshop: **the multi-agent pattern in this demo is not tool-specific.** Whatever coding agent you use, you can define these specialists — and the same idea powers larger research systems (e.g. Hermes delegation in Demo 5).

## What is new here

This is where the workflow becomes about **specialization + verification**, not just "thinking harder." The provenance table — conclusion → evidence artifact → notebook source → confidence → caveat — is the point.

## Audience question

If an agent says the data support a paper's central conclusion, what would you want to inspect before trusting it?


