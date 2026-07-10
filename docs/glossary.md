# Glossary

Minimal shared vocabulary for the workshop.

- **LLM** — the model that generates text by predicting the next token.
- **Context** — the information currently available to the model: prompt, documents, conversation history, retrieved material.
- **Tool** — an external capability the model can call: search, code execution, database query, an API.
- **Agent** — an LLM + context + tools + a loop for taking actions and checking the results.
- **Pipeline** — a fixed sequence of steps that runs the same way every time.
- **Routine** — a packaged, reusable workflow that an agent can run on a schedule or on demand; more flexible than a pipeline, more repeatable than an ad-hoc chat.
- **Copilot** — an assistant that works *in the loop* with you: you stay in control, it accelerates each step.
- **Autonomous agent** — a system that acts on its own toward a goal, calling tools and checking its work with limited human intervention.
- **MCP (Model Context Protocol)** — one standard protocol that lets an agent connect to external systems (databases, lab notebooks, literature APIs, Drive, Slack). The agent discovers each server's tools when it connects.
- **Local tools** — tools that run where the model runs (your machine or a sandbox): code execution, file read/write, local search.
- **Skill** — a reusable, saved procedure the agent can load into a future session.
- **Memory** — durable state the agent keeps across sessions: your preferences, prior feedback, environment facts.
- **Artifact** — a concrete, inspectable output of a run (a memo, notebook, digest, table) — the thing you can open and check.

## The spectrum of agentic behavior

These describe not only how a system is *built*, but how you *use* it. The same tool can be run in different modes.

```text
Chat            Copilot                 Autonomous agent
AI responds  →  AI assists in the loop  →  AI acts by itself toward a goal
(more human control)  ────────────────►  (more agent action & initiative)
```

