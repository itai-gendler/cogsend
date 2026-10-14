---
appliesTo:
  - { type: entity, id: tick-token, effect: creates }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/routes/api/scheduler/tick-token/+server.ts }
---

# Only the signed-in Admin generates the tick token

The tick token is generated only from Settings in a signed-in browser.
