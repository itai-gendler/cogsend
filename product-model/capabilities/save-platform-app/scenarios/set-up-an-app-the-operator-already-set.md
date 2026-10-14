---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin tries to save app details for a platform the operator set up with Worker secrets
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product refuses, since the Worker secrets take precedence
    kind: condition
    entities:
      - { entity: platform-app, effect: reads, facts: [Source] }
    contexts: { web: { place: web::app::accounts } }
---

# Set up an app the operator already set

## Trigger

The Admin forgot the app is already configured on the deployment.

## Outcome

The Worker secrets stay in use.
