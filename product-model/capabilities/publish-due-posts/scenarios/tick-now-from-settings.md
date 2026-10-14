---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin presses Tick now under Scheduled publishing
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product runs a tick at once, publishing what is due, and says how many it processed
    kind: product
    actor: admin
    entities:
      - { entity: instance, effect: changes, facts: [Last tick] }
      - { entity: delivery, effect: changes, from: Scheduled, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Scheduled, to: Published, facts: [] }
    contexts: { web: { place: web::app::settings } }
---

# Tick now from Settings

## Trigger

The Admin wants to know whether the app side of scheduling works.

## Outcome

Due posts are published and the Admin can tell the app is not the problem.
