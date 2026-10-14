---
appliesTo:
  - { type: entity, id: tick-token, effect: removes }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/routes/api/scheduler/tick-token/+server.ts }
---

# Only the signed-in Admin revokes the tick token

The tick token is revoked only from Settings in a signed-in browser.
