# Demo 4 — literature radar

## Point of the demo

Show a recurring scientific workflow where an agent adds value by handling **variation** across many incoming papers while still producing something easy for a human to verify.

This is the cleanest example in the repo of the pattern:

> signal arrives -> context is gathered -> papers are triaged -> interesting items are escalated -> a human reviews the memo

## Why this is a strong workshop demo

- scientists instantly understand the problem
- the inputs vary every run
- the output can be checked quickly
- there is a natural escalation point back to the human
- it demonstrates that the value is not "AI reads papers" but **AI helps manage attention**

## What to show live

- where candidate papers come from
- what the triage criteria are
- what gets rejected early
- what gets escalated
- what the final memo / digest looks like

## Good framing

This is **not** a pipeline that simply dumps summaries. The agentic part is that the system has to decide what is interesting, what is weak, and what deserves human attention.

## What to stress

- novelty filters matter
- ranking criteria matter
- the final artifact has to be reviewable by a scientist
- bad triage is often more dangerous than bad prose

## Files

The implementation scaffold for this demo lives in the nested repo:
- `lit-radar/`

