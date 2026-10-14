---
type: webhook
actors: [external-cron]
entryPoints:
  - webhook: /api/internal/tick
references:
  - { kind: doc, role: intent, target: docs/scheduling.md, title: Scheduling }
  - { kind: code, role: implementation, target: src/routes/api/internal/tick/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/require.ts#assertSchedulerOrTickToken }
---

# Scheduler tick

The address an external cron posts to, once a minute or at its own cadence,
so that whatever has come due is published.
