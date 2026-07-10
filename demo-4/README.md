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

That repo packages the minimal core: mining papers, ranking/triage, Notion sync, and an editable topic-lens that captures preferences over time. It sets up Demo 5.

## Audience question

What would you want your own reusable routine to watch or produce?

