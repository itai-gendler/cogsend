---
appliesTo:
  - { type: entity, id: delivery, effect: removes }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: "src/routes/api/connections/[id]/+server.ts" }
---

# Only the signed-in Admin removes deliveries of an account

An account's unpublished deliveries are removed when the signed-in Admin disconnects it; deleting a post takes its deliveries with it.
