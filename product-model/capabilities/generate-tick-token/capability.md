---
availability:
  - { place: web::app }
domain: settings
references:
  - { kind: code, role: implementation, target: src/routes/api/scheduler/tick-token/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/tick-token.ts#rotateTickToken }
  - { kind: doc, role: intent, target: docs/scheduling.md, title: "Pick one tick" }
---

# Generate a tick token

Create the credential an external cron uses to call the tick, under Settings, Scheduled publishing. It is shown once, works for the tick and nothing else, and a replacement stops the old one.
