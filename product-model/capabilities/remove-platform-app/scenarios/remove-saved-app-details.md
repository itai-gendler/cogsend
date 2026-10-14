---
kind: primary
routes:
  web: Web
steps:
  - text: "The Admin presses Remove on a platform's saved app details"
    kind: actor
    actor: admin
    entities:
      - { entity: platform-app, effect: reads, facts: [Platform, Client ID] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Product deletes the platform app and the platform shows Needs setup again
    kind: product
    actor: admin
    entities:
      - { entity: platform-app, effect: removes }
    contexts: { web: { place: web::app::accounts } }
---

# Remove saved app details

## Trigger

The Admin is replacing or retiring a developer app.

## Outcome

No app details are stored for that platform.
