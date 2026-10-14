---
availability:
  - { place: web::app }
references:
  - { kind: code, role: implementation, target: src/routes/+page.server.ts }
  - { kind: code, role: implementation, target: src/lib/server/scheduler.ts#schedulerHealth }
  - { kind: code, role: implementation, target: src/routes/api/scheduler/health/+server.ts }
  - { kind: code, role: implementation, target: src/lib/domain/scheduler-status.ts }
---

# See publishing health

See whether scheduled publishing works: on the dashboard, a health line and counts of drafts, scheduled and failed posts; under Settings, Scheduled publishing, when ticks last arrived and what to do if they do not.
