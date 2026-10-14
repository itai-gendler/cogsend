---
appliesTo:
  - { type: entity, id: platform-app, effect: creates }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: "src/routes/api/settings/platform-apps/[platform]/+server.ts" }
---

# Only the signed-in Admin sets up platform apps

Developer app details are entered only in the accounts dialog of a signed-in browser.

## Rationale

A key or agent must not be able to point the connect flow at an app somebody else controls.
