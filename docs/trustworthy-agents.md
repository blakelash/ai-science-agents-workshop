# What Trustworthy Agent Demos Have in Common

The anti-hype point of the workshop:

> These demos worked because they could be **checked** — not because the model was clever.

Five properties separated the trustworthy demos from impressive-but-unverifiable ones:

1. **Inspectable artifacts** — every step leaves something you can open and read.
2. **External checks** — verification against the paper, the data, or a second reviewer, not the model's own say-so.
3. **Bounded scope** — each agent had a *job*, not a *mission*.
4. **Visible failure modes** — we named what going wrong looks like, out loud, in advance.
5. **Explicit escalation paths** — a human knows exactly when to take over.

## How this maps to the seven-box lens

| Trust property | Seven-box box |
|---|---|
| Inspectable artifacts | **Artifact** |
| External checks | **Check** |
| Bounded scope | **Agent needs** + **Tools / access** |
| Visible failure modes | **Failure modes** |
| Explicit escalation paths | **Escalation** |

If a proposed agent workflow can't satisfy these five, it isn't ready for autonomy — narrow the scope, add a check, or keep a human in the loop.

