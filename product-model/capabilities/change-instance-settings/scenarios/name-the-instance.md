---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin enters a name under Instance and presses Save
    kind: actor
    actor: admin
    entities:
      - { entity: instance, effect: reads, facts: [] }
    contexts: { web: { place: web::app::settings } }
  - text: "The Product keeps it as the Instance's name, shown in the page title, the header and the login screen"
    kind: product
    actor: admin
    entities:
      - { entity: instance, effect: changes, facts: [Name] }
    contexts: { web: { place: web::app::settings } }
---

# Name the instance

## Trigger

The Admin runs more than one instance or wants their own name on it.

## Outcome

Every page and the login screen carry the new name.

## Edge cases

- An empty name goes back to CogSend.
