---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin ticks Offer pre-releases too
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product keeps the choice and offers release candidates as updates too
    kind: product
    actor: admin
    entities:
      - { entity: instance, effect: changes, facts: [Offer pre-releases] }
    contexts: { web: { place: web::app::settings } }
---

# Offer pre-releases

## Trigger

The Admin wants to test a release before it is published.

## Outcome

Update notices include release candidates.
