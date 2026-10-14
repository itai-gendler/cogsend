---
appliesTo:
  - { type: capability, id: schedule-post }
  - { type: capability, id: publish-post }
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#scheduleDraft }
  - { kind: code, role: implementation, target: src/lib/domain/post-state.ts#selectionDrift }
---

# Scheduling from the composer goes to exactly the accounts ticked

Scheduling or publishing now from the composer cancels the waiting deliveries of accounts that are no longer ticked, so an unticked account never posts later.
