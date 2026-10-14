---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin presses Post again on a published card
    kind: actor
    actor: admin
    entities:
      - { entity: post, as: original, effect: reads, facts: [Text] }
      - { entity: delivery, effect: reads, facts: [Link] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product creates a Draft copy without any deliveries and opens it in the composer
    kind: product
    actor: admin
    entities:
      - { entity: post, as: copy, effect: creates, to: Draft, facts: [Title, Text, Selected accounts, Last edited] }
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Post a published post again

## Trigger

The Admin wants to share the same thing again.

## Outcome

A fresh draft of it is ready to publish or schedule.
