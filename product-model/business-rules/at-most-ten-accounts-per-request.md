---
appliesTo:
  - { type: capability, id: publish-post }
  - { type: capability, id: schedule-post }
  - { type: capability, id: retry-delivery }
  - { type: capability, id: reschedule-delivery }
  - { type: capability, id: cancel-delivery }
references:
  - { kind: code, role: implementation, target: src/lib/domain/request-limits.ts }
  - { kind: code, role: implementation, target: src/routes/api/targets/bulk/+server.ts }
---

# One request acts on at most ten accounts

A publish or schedule request names at most ten accounts, and one action on a card in Posts covers at most ten deliveries. The composer publishes one account per request, but schedules all ticked accounts in one, so scheduling more than ten ticked accounts at once is refused with Too many connections (max 10).
