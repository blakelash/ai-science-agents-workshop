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

A routine is just a thin wrapper that calls the modules on a schedule — but the *lens* is personal. This example is framed around a real paper: **PTER** (Wei et al., *Nature* 2024, [s41586-024-07801-6](https://doi.org/10.1038/s41586-024-07801-6)) showed that the orphan enzyme PTER hydrolyzes N-acetyltaurine and that blocking it (Pter knockout / NAT administration) suppresses feeding and diet-induced obesity via GFRAL — a weight-loss mechanism with **nothing to do with GLP-1**.

So the routine's job is: *"I thought PTER was a cool paper. Keep me alerted to new non-GLP1 obesity advances — especially anything moving PTER toward a drug, like an oral PTER inhibitor."*

Point Claude Code at the `lit-radar/` skills and give it a prompt like this (save as a scheduled routine / `/skill`, or run daily via cron):

```text
You are running my Literature Radar monitoring routine. The skills and specs are
in ./lit-radar (the literature-radar-skills repo).

MY LENS (why I care): I loved the PTER paper (Nature 2024, s41586-024-07801-6) —
PTER / N-acetyltaurine / GFRAL is an anti-obesity mechanism that is NOT GLP-1-based.
I want to be alerted to advances on the non-GLP1 obesity frontier, and especially
to anything pushing this axis toward a therapeutic: a PTER inhibitor (bonus if oral),
N-acetyltaurine or taurine-axis pharmacology, GFRAL/GDF15 agonists, or other novel
central/peripheral appetite or energy-balance targets. DEPRIORITIZE incremental
GLP-1 / GIP / amylin analog papers unless they reveal genuinely new biology.

Do the following once:

1. MINE — using docs/data-sources.md and templates/journal_feeds.json, fetch the
   last 2 days of new papers from the journal RSS feeds (run
   scripts/fetch_journal_rss.py), plus bioRxiv/medRxiv (version==1 only) and
   OpenAlex. Normalize every item to templates/candidate-schema.json and dedupe
   by DOI → canonical URL → title.

2. RANK — apply docs/ranking-rubric.md, but bias the lens toward MY interest above:
   non-GLP1 obesity / appetite / energy-balance biology with a plausible, undeveloped
   therapeutic angle and causal evidence. Run the recall-first prefilter, then the
   four-question triage on survivors. Keep only Tier 1 and Tier 2; drop the rest.
   Emit the fields in templates/scored-schema.json, and for each paper write a
   2-sentence `why` (strongest positive + limiting caveat). A credible step toward
   an oral PTER inhibitor is an automatic Tier 1.

3. WRITE — follow docs/notion-spec.md exactly. If the Literature Radar database does
   not exist yet, create it (title-only shell → PATCH schema onto the data source →
   rows via data_source_id). Add one row per retained paper. ALWAYS also write a local
   digest.md ordered by tier, then Score descending.

Rules: lens = new/underexploited biology with an undeveloped therapeutic angle and
causal evidence — not "good paper," not journal prestige. Source label = the journal,
never "OpenAlex." If NOTION_API_KEY is missing, skip the Notion write but still
produce digest.md. Finish with a one-line summary: "X Tier-1, Y Tier-2 from N scanned."
```

Keep the runner thin: it orchestrates mine → rank → write and nothing more. The scientific logic stays in the skills, not the routine. See `lit-radar/examples/runners/` for the same idea under Hermes cron and a plain script.

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





