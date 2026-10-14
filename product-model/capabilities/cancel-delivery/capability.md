---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#cancelDelivery }
  - { kind: code, role: implementation, target: src/routes/api/targets/bulk/+server.ts }
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
---

# Cancel a delivery

Take a post off the schedule: Cancel on a scheduled card cancels each of its accounts, Unschedule in the composer turns the post back into a draft, and scripts and agents cancel one delivery.
