---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin presses the bin in the composer on a scheduled post and confirms
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product deletes the post with its scheduled deliveries, so it will not be published
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: removes, from: Scheduled }
      - { entity: delivery, effect: removes, from: Scheduled, with: post }
    contexts: { web: { place: web::app::composer } }
---

# Discard a scheduled post with the bin

## Trigger

A scheduled post should not go out after all.

## Outcome

The post is gone and nothing will be published.
