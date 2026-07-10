# Demo 4 — Monitor / Reusable Routine

## Surface

Claude Code routines.

## Scientific job

Package the literature-radar workflow into a **reusable routine** / repo of instructions, skills, configs, rubrics, and output formats.

## Inputs

- topic or target area
- sources list
- scoring rubric

## What the system needs

- stable reusable workflow components
- versioned routine logic

## Tools / access needed

- repo + routine surface
- sources
- configs
- scoring files
- digest output

## Artifact

A routine repo with pieces like:
- `README`
- `skills/`
- `config/`
- `outputs/digest.md`

## Why this new surface is needed

By this point, the workflow is stable enough that it should be **reused, versioned, and inspectable** rather than rerun ad hoc each time.

## Check / failure mode

- **Failure mode:** reusable routine, but noisy or opaque outputs
- **Check:** results are deduplicated, relevance reasons are specific, weak papers are excluded, and the routine is inspectable by another person

## Audience question

- What would you want your own reusable routine to watch or produce?

## What is new here

This step introduces **recurrence and monitoring over time**, not just one-off analysis.

## Files

The implementation scaffold for this demo lives in the nested repo:
- `lit-radar/`

