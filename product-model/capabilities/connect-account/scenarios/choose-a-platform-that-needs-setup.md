---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin chooses a platform marked Needs setup in the picker
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: No platform app is set up for it, so the Product shows its redirect address and the app details to provide, and a way to connect through Zernio instead, without attempting to connect
    kind: condition
    entities:
      - { entity: platform-app, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::accounts } }
---

# Choose a platform that needs setup

## Trigger

The Admin picks LinkedIn, Threads or X on a fresh instance.

## Outcome

No connection is attempted that cannot succeed; the Admin knows what to set up.
