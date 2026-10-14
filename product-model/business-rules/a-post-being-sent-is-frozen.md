---
appliesTo:
  - { type: capability, id: edit-post }
  - { type: capability, id: delete-post }
  - { type: capability, id: disconnect-account }
  - { type: capability, id: edit-platform-override }
  - { type: capability, id: attach-image }
references:
  - { kind: code, role: implementation, target: src/lib/server/publish-plan.ts#draftHasInFlightPublish }
  - { kind: code, role: implementation, target: src/lib/domain/published-lock.ts }
---

# A post being sent cannot be changed or deleted

While any of a post's deliveries is being sent, its text, overrides and images do not change, the post cannot be deleted, and its account cannot be disconnected; the answer is Publishing in progress, try again shortly.

## Rationale

Publishing reads the post as it is when each card goes out; changing it underneath would send a mix.
