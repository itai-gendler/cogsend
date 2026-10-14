---
references:
  - { kind: code, role: implementation, target: src/lib/server/tick-token.ts }
  - { kind: code, role: implementation, target: src/routes/api/scheduler/tick-token/+server.ts }
---

# Tick token

The credential the Admin generates for an external cron. It is accepted only
by the tick and by nothing else; there is at most one, and a replacement stops
the old one.

## Information kept

- **Prefix** — the first characters, shown so the token can be recognised; the full token is shown once and only its hash is kept
- **Created** — when it was generated
