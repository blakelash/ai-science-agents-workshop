# Demo 4 — Monitor with a Reusable Routine

**Surface:** Claude Code (routines) · *other options: scripts + scheduler, CI jobs*

**New capability:** routines (runs on its own), interaction with external DBs / surfaces, skills.

## Goal

Package a stable workflow into a **reusable monitoring routine** — one that watches for new work, filters and ranks it, and produces a legible digest a scientist can review.

## Seven-box lens

| Box | Answer |
|---|---|
| **Inputs** — what goes in? | New papers from feeds, daily |
| **Agent needs** — what must it do? | Filter, rank, dedupe, explain |
| **Tools / access** — what can it touch? | Feeds + a repo of skills and rubrics |
| **Artifact** — what appears at the end? | A digest: a shortlist with reasons |
| **Check** — how do we verify it? | Deduped, selective, legible output |
| **Escalation** — when does a human take over? | A human reads the digest before acting on it |
| **Failure modes** — what does going wrong look like? | Noisy confidence, duplicates, weak papers slipping through |

## What is new here

This step introduces **recurrence and monitoring over time**, not one-off analysis. The workflow is now stable enough to be *reused, versioned, and inspectable* rather than rerun ad hoc — a packaged asset instead of a fresh chat each time.

## Files

The implementation for this demo lives in the real literature-radar repo, mounted here as a submodule:

- `lit-radar/` → [`blakelash/literature-radar-skills`](https://github.com/blakelash/literature-radar-skills)

That repo packages the minimal core: mining papers (journal RSS + preprints + OpenAlex), ranking/triage against a fixed rubric, and a write-only Notion sink. It is deliberately monitoring-only — memory and preference-learning are Demo 5's job.

## Example Claude Code routine prompt

A routine is just a thin wrapper: the skills in `lit-radar/` carry all the how-to (mining, ranking, Notion), so the prompt only has to supply **your lens** and say "follow the skills."

This example is framed around a real paper: **PTERi** — a first-in-class small-molecule PTER inhibitor ([Long lab, bioRxiv 2026](https://www.biorxiv.org/content/10.64898/2026.01.26.701829v1)). PTER is an amidohydrolase that degrades the appetite-suppressing metabolite N-acetyltaurine; inhibiting it reduces feeding, **boosts GLP-1-RA weight loss, and prevents regain after the GLP-1 drug is stopped**. It's a novel *non-incretin* obesity mechanism — differentiated from, and complementary to, the crowded GLP-1 field.

So the routine's job is: *"I loved the PTERi paper. Keep me alerted to new non-incretin obesity biology and anything advancing druggable metabolite/enzyme axes like this one."*

Point Claude Code at the attached `lit-radar/` skills and give it a prompt like this (save as a scheduled routine / `/skill`, or run daily via cron):

```text
Run my Literature Radar routine using the skills in ./lit-radar
(github.com/blakelash/literature-radar-skills) — follow their guidance for mining,
ranking, and writing to Notion. Do one pass for the last 2 days.

Make yourself a home in my Notion: on the first run, create your own page and a
Literature Radar database under it and remember them; on later runs, reuse them.
Before adding anything, check Notion for papers you already recorded and skip those —
only add genuinely new ones.

MY LENS: I loved the PTERi paper (small-molecule PTER inhibitor, bioRxiv 2026,
10.64898/2026.01.26.701829). I want novel NON-INCRETIN obesity / appetite /
energy-balance biology with a real druggable handle and causal evidence —
especially druggable metabolite or enzyme axes (like PTER / N-acetyltaurine) and
anything that complements or de-risks weight-loss beyond GLP-1. Deprioritize
incremental GLP-1 / GIP / amylin analog papers unless they show genuinely new biology.
A credible new PTER-axis or non-incretin obesity drug lead is an automatic Tier 1.

If NOTION_API_KEY is missing, skip the Notion write but still produce digest.md.
End with a one-line summary: "X Tier-1, Y Tier-2 from N scanned."
```

That's the whole point of packaging the workflow as skills: the runner prompt stays short and personal, while the reusable logic lives in `lit-radar/`. See `lit-radar/skills/research/literature-radar/references/runner-examples.md` for the same routine under Hermes cron or a plain script.

> Note the deliberate limitation: this routine re-reads your lens from the prompt every run — it does **not** remember your reactions to yesterday's digest. Teaching it to learn "you already showed me that / more like this one" is exactly the jump to Demo 5.

## Skills — a primer

A **skill** is a reusable, packaged procedure an agent can load when it's relevant. In practice it's a folder with a `SKILL.md` file: YAML frontmatter (a `name` and a `description` of *when to use it*) plus a Markdown body with the step-by-step instructions, and optionally supporting `scripts/`, `references/`, and `assets/`.

```markdown
---
name: bulk-rnaseq-de
description: Run a bulk RNA-seq differential-expression analysis (FASTQ → counts → DE → enrichment). Use when the user has RNA-seq count data and wants DE results.
---

## Steps
1. QC and align/quantify (or start from a counts matrix)
2. Normalize and run differential expression (e.g. PyDESeq2)
3. Functional enrichment (ORA / GSEA)
4. Write a short results memo with the key genes and pathways
```

### Why skills matter (especially for Demo 4)

- **They encode a workflow once** so it runs the same way every time — this is exactly what turns an ad-hoc chat into a *reusable routine*.
- **Progressive disclosure:** only the short description sits in context by default; the full body loads only when the skill is actually triggered, so a big library costs almost nothing until used.
- **Composability:** an agent can combine several small, focused skills for one task. Many small skills beat one giant skill.
- **Portability:** skills are just Markdown files, so the same skill often works across agents.

### When to make one

Make a skill when you keep pasting the same instructions or checklist into chat, when a procedure has become stable enough to reuse, or when you want a workflow to run identically for you and your collaborators. Keep each skill **focused on one workflow**, write a **specific description** (the agent uses it to decide when to load the skill), and start with plain instructions before adding scripts.

### The open standard

Skills follow an open **Agent Skills** specification (https://agentskills.io/), so a well-written `SKILL.md` works across Claude Code, Cursor, Codex, Gemini CLI, OpenClaw, Hermes, and more — not just one vendor.

Docs:
- **Agent Skills overview (Anthropic):** https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview
- **Creating custom skills:** https://claude.com/docs/skills/how-to
- **Authoring best practices:** https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices
- **Open spec:** https://agentskills.io/

### Open-source scientific skill libraries

You don't have to start from scratch — there are large, open libraries of science skills you can install and adapt:

- **Scientific Agent Skills** (K-Dense, MIT, ~148 skills + 100+ databases; works with Claude Code, Cursor, Codex, Hermes, etc.): https://github.com/K-Dense-AI/scientific-agent-skills
- **SciAgent-Skills** (199 bioinformatics/life-science skills — RNA-seq, single-cell, proteomics, drug discovery): https://github.com/jaechang-hits/SciAgent-Skills
- **bioSkills** (GPTomics — bioinformatics skills across many categories): https://github.com/GPTomics/bioSkills
- **awesome-bio-agent-skills** (curated index aggregating skills from many repos): https://github.com/BioTender-max/awesome-bio-agent-skills

> The literature-radar submodule in this demo is itself a small skill suite (mining / ranking / Notion-sync) — a concrete example of packaging a scientific workflow as skills.

## Audience question

What would you want your own reusable routine to watch or produce?










