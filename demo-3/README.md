# Demo 3 — bounded agent

## Point of the demo

Move from *"tell me what you think"* to *"take a bounded action sequence and come back with a result."*

This is the first demo that should feel clearly **more agentic** than demo 2.

## Core design rule

Use a task that is:
- variable enough that a fixed pipeline is awkward
- verifiable enough that success or failure is visible
- bounded enough to run live without magic

## Good candidate task shapes

- inspect a paper/repo and produce a structured opportunity memo
- intake a scientific question and draft a reproducible analysis plan
- gather a few sources, compare them, and produce a ranked next-step recommendation
- run a short multi-step retrieval → synthesis → verification loop

## Live arc

1. Give the system a concrete goal.
2. Give it explicit tools or sources it is allowed to use.
3. Tell it what counts as a valid output.
4. Let it perform a short sequence of steps.
5. Review the returned memo and check whether it met the criteria.

## Suggested framing line

> The difference here is not that the model got smarter; it is that we delegated a small amount of process control.

## What to emphasize

- the system is not doing open-ended science
- the task is bounded and observable
- the interesting part is the **loop**: inspect, decide, act, check, report
- validation is part of the demo, not an afterthought

## Validation ideas

- did it use the allowed sources?
- did it answer the requested question?
- did it produce the requested schema or memo format?
- did it flag uncertainty where evidence was thin?
- can a human quickly inspect whether the recommendation is reasonable?

## Failure modes to mention

- wandering outside scope
- doing too much instead of returning a clean partial result
- hiding uncertainty
- failing silently when a source/tool is weak

## Take-home message

Agents are most compelling when they add **bounded judgment around reliable steps**, not when they pretend to be autonomous scientists.

