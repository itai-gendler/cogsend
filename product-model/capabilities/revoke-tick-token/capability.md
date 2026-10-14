---
availability:
  - { place: web::app }
domain: settings
references:
  - { kind: code, role: implementation, target: src/routes/api/scheduler/tick-token/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/tick-token.ts#revokeTickToken }
---

# Revoke the tick token

Stop the tick token, so an external cron using it stops publishing at once.
