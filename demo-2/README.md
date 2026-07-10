# Demo 2 — Contextualize

**Surface:** Claude Cowork + Paperclip · *other options: NotebookLM, Elicit, PaperQA2 / Edison Lit*

**New capability:** tool use — content retrieval via an MCP server.

## Goal

Place the paper in its wider scientific context: novelty, related work, competition, and uncertainty.

## Seven-box lens

| Box | Answer |
|---|---|
| **Inputs** — what goes in? | The paper + literature retrieval |
| **Agent needs** — what must it do? | Search, compare, and cite related work |
| **Tools / access** — what can it touch? | Web + literature search |
| **Artifact** — what appears at the end? | A context memo with citations |
| **Check** — how do we verify it? | Citations resolve to real papers |
| **Escalation** — when does a human take over? | Before repeating any novelty claim |
| **Failure modes** — what does going wrong look like? | False novelty, invented context |

## What is new here

This is the jump from *"read this paper well"* to *"situate this paper in the field."* The point is not better summarization — it is that the paper alone is almost never enough context for scientific judgment. This is also the first demo where the agent uses a **tool** (retrieval via MCP) rather than just reasoning over what it was handed.

## Tools & MCP servers — the primer

This is where the workshop introduces **tools**: external capabilities the model can call (search, code execution, database queries, an API). Two flavors matter:

- **Local tools** — run where the model runs (your machine or a sandbox): code execution, file read/write, local search. Example: run Python on a CSV, grep a repo, edit a file.
- **MCP servers** — one standard protocol (the **Model Context Protocol**) that connects an agent to external systems: databases, lab notebooks, literature APIs, Drive, Slack. Think of MCP as "a USB-C port for AI apps." The agent *discovers* each server's tools when it connects, so you can add new capabilities without rebuilding the agent.

MCP has a simple client–server shape: your AI app (the **host**) opens a connection to one or more **MCP servers**, each exposing a set of tools. Servers can run **locally** (stdio transport) or **remotely** (HTTP). In this demo, literature retrieval comes in through an MCP server rather than being pasted into the prompt.

### Learn MCP

- **What is MCP (official intro):** https://modelcontextprotocol.io/docs/getting-started/intro
- **Architecture overview:** https://modelcontextprotocol.io/docs/learn/architecture
- **Official MCP registry (about):** https://modelcontextprotocol.io/registry/about
- **GitHub org + reference servers:** https://github.com/modelcontextprotocol

### Where to find MCP servers (marketplaces / directories)

- **Official MCP Registry:** https://registry.modelcontextprotocol.io/
- **MCP.Directory:** https://mcp.directory/
- **MCP Marketplace:** https://mcp-marketplace.io/browse
- **MCPFind:** https://www.mcpfind.org/
- **Cursor Directory:** https://cursor.directory/

### Connecting tools in the major surfaces

Almost every AI tool now has its own way to add MCP servers / connectors — often with a built-in marketplace:

- **Claude (Anthropic) — Connectors Directory:** https://claude.ai/connectors · docs: https://claude.com/docs/connectors/overview
- **ChatGPT (OpenAI) — Apps / connectors & developer mode:** https://developers.openai.com/apps-sdk/deploy/connect-chatgpt · MCP guide: https://developers.openai.com/api/docs/guides/tools-connectors-mcp
- **Cursor — MCP:** https://cursor.com/docs/mcp
- **VS Code — MCP servers:** https://code.visualstudio.com/docs/agent-customization/mcp-servers

> Tip: most servers install with a single `npx` (Node) or `uvx` (Python) command, then a small JSON config block in your client. Prefer `npx`/`uvx` so dependencies resolve automatically.

In this demo, the retrieval capability is provided by **Paperclip**, the retrieval MCP server (https://paperclip.gxl.ai/) — literature comes in through that server rather than being pasted into the prompt. *Other retrieval options: NotebookLM, Elicit, PaperQA2 / Edison Lit.*

## Audience question

What outside context would most change your opinion of a new paper?



