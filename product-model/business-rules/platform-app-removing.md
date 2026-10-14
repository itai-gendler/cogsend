---
appliesTo:
  - { type: entity, id: platform-app, effect: removes }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: "src/routes/api/settings/platform-apps/[platform]/+server.ts" }
---

# Only the signed-in Admin removes platform apps

Saved developer app details are removed only in the accounts dialog of a signed-in browser.
