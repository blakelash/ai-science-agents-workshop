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

## How you'd ask for it

The Demo 4 routine was a *structured* prompt pointed at a fixed skill. With a durable collaborator, you can just **describe what you want in plain language** and let it set itself up. This is (paraphrased) the actual ask that produced the tracker for this demo:

> *"Keep me up to date on the literature around non-GLP1 anti-obesity drugs. I found a cool recent paper on small-molecule PTER inhibitors (a non-GLP-1R axis) — survey the field daily for new work like it. Make a Notion page and database to track it, and leave space for **me to give feedback on each paper**, plus room to note **deep dives** on the axis and **computational projects** to explore. If you read something especially interesting and see a clear computational project to extend it, **ping me and come with a plan** — you don't have to every time, just when it's worth it."*

Notice what's in there beyond Demo 4's "mine → rank → write": a place for **feedback**, standing **instructions** that should persist, **project ideas** to accumulate, and a **conditional, judgment-based escalation** ("ping me *when it's worth it*, with a plan"). None of that survives in a stateless routine — it only works if the system *remembers* across runs. That is the jump this demo is about.

## Memory — how a system like Hermes learns

"Memory" here is not one feature; it's a few layers that together let a collaborator improve instead of just repeat:

| Layer | What it holds | How it changes behavior |
|---|---|---|
| **User profile** | Durable facts about you and your taste (e.g. "cares about causal/translational support; rejects correlational-only") | Injected into every future run, so the lens sharpens without re-explaining |
| **Agent memory** | The system's own notes — environment facts, conventions, lessons learned | Stops it repeating mistakes and re-discovering the same setup |
| **Skills** | Reusable procedures it writes down after doing something non-trivial | Later tasks reuse the procedure; a background *curator* keeps skills fresh and retires stale ones |
| **Project state / the Notion DB** | Feedback, verdicts, deep-dive notes, project ideas, what's already been shown | Read back on the next run to adapt ranking and avoid repeats |

The loop that makes it a *collaborator*:

1. **It acts** — surveys, ranks, writes the digest.
2. **You react** — a verdict, a comment, "more like this," "stop showing me X," "go deep on the PTER axis."
3. **It updates** — promotes recurring feedback into the user profile / lens, refines the skill, records standing instructions and project ideas.
4. **Next run is different** — the shortlist reflects what you taught it, and it can *proactively* flag "this one's worth a computational project — here's a plan."

Two failure modes to watch (see the seven-box lens): **decorative memory** (feedback is stored but the output never changes) and **overfitting** (one old comment dominates forever). Good memory is visible — you should be able to point at a change in today's shortlist and trace it to something you said last week.

> The contrast with Demo 4 in one line: a **routine re-reads the same lens every run**; a **collaborator rewrites the lens from your feedback** and carries instructions, project ideas, and history forward. Demo 4's Notion sink already *dedupes* against what it wrote before — Demo 5 goes further and *learns* from what you thought of it.

Docs: [Hermes memory](https://hermes-agent.nousresearch.com/docs/user-guide/features/memory) · [skills / curator](https://hermes-agent.nousresearch.com/docs/user-guide/features/curator)

## Audience question

What feedback would you actually be willing to give a system so that it improves over time?


