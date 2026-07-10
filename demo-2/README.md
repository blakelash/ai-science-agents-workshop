# Demo 2 — exploratory copilot

## Point of the demo

Show the lowest-friction useful behavior: you can hand an AI system a paper, repo, website, methods section, or dataset landing page and say, essentially, *"go take a look and tell me what matters."*

This is not full autonomy. It is a **copilot / reconnaissance** mode.

## What this demo should show

- fast orientation on unfamiliar material
- extraction of the key claims, structure, and unknowns
- a first-pass recommendation for what to inspect next
- clear separation between **summary**, **interpretation**, and **speculation**

## Live arc

1. Give the system one artifact: paper, repo, site, protocol, or folder.
2. Ask for a quick map of what is there.
3. Ask what looks important versus routine.
4. Ask what the best next inspection step is.
5. Ask what the system is still uncertain about.

## Good prompt shape

> Go take a look at this and give me a practical orientation memo. What is this? What are the main claims or components? What seems important versus boilerplate? What would you inspect next if your goal were to understand whether there is a real scientific opportunity here?

## Why this belongs in the workshop

This is the easiest on-ramp for scientists: it is useful immediately, requires very little setup, and illustrates that a lot of value comes from **structured reconnaissance**, not just polished text generation.

## What it teaches

- where chat/copilot mode is already enough
- how much value you can get before building an agent
- that human judgment still sets the objective and evaluates the takeaways

## Failure modes to mention

- confident but shallow summaries
- over-weighting the abstract or README and missing the supplement/details
- confusing novelty with importance
- making recommendations without showing evidence

## What a good output looks like

A short memo with:
- the core claim / structure
- the 2-3 most important things to inspect next
- explicit uncertainty
- one suggested follow-up action

