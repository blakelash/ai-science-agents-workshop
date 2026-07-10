# Demo 5 — Adapt with Memory

**Surface:** Hermes · *other options: orchestration + memory systems*

**New capability:** memory — the system learns your preferences and adapts.

## Goal

A routine *repeats*; a collaborator *remembers and adapts*. Turn the Demo 4 routine into a persistent collaborator that carries feedback, preferences, and exclusions across runs.

## Seven-box lens

| Box | Answer |
|---|---|
| **Inputs** — what goes in? | Digests + my feedback over time |
| **Agent needs** — what must it do? | Store, recall, and apply preferences |
| **Tools / access** — what can it touch? | Memory + the monitoring routine |
| **Artifact** — what appears at the end? | A before/after shortlist, with reasons |
| **Check** — how do we verify it? | Feedback visibly changes the output |
| **Escalation** — when does a human take over? | When preferences conflict or drift |
| **Failure modes** — what does going wrong look like? | Decorative memory — it exists but nothing changes; or overfitting one old preference |

## Reusable routine vs. collaborator

| Capability | Reusable routine | Hermes / memory layer |
|---|---|---|
| Reusable workflow | yes | yes |
| Durable memory | limited | yes |
| Feedback history | awkward / manual | yes |
| Cross-run adaptation | limited | yes |

## What is new here

This demo introduces **memory + adaptation**. The point is not recurring automation — it is relationship-building over time. The system becomes more aligned with the scientist's taste and workflow: reject review articles, prefer human genetic support, care about structural tractability, deprioritize mouse-only incrementals — and it should be able to *show you* exactly what prior feedback changed.

Hermes is a top-level orchestrator that is persistent and durable: memory, skills, state, tool use, and subagents, reachable across many surfaces. It generates memory, skills, and tasks on demand, and uses your feedback to improve skills so later tasks get easier.

## Audience question

What feedback would you actually be willing to give a system so that it improves over time?

