---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: posts
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#rescheduleDelivery }
  - { kind: code, role: implementation, target: src/routes/api/targets/bulk/+server.ts }
  - { kind: code, role: implementation, target: src/routes/posts/+page.svelte }
---

# Reschedule a delivery

Move a scheduled post to another time from its card in Posts, by an offset or to a specific time; scripts and agents move one delivery. A rescheduled delivery starts its automatic attempts afresh.
