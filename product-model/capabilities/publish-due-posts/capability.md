---
availability:
  - { place: web::app }
  - { place: scheduler-tick }
references:
  - { kind: code, role: implementation, target: src/lib/server/scheduler.ts#runSchedulerTick }
  - { kind: code, role: implementation, target: src/lib/server/scheduler.ts#claimDueTargets }
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#publishTarget }
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#retryDelayMs }
  - { kind: code, role: implementation, target: src/routes/api/internal/tick/+server.ts }
  - { kind: code, role: implementation, target: src/routes/api/scheduler/test/+server.ts }
  - { kind: doc, role: intent, target: docs/scheduling.md, title: "How a tick works" }
---

# Publish due posts

On each tick, publish every delivery whose time has come, oldest first, as far as the request's call budget allows; the rest wait for the next tick. A tick comes from the Worker's own cron every minute, from an external cron calling the tick address, or from Tick now in Settings. Temporary failures retry on their own with growing waits, five attempts in all.
