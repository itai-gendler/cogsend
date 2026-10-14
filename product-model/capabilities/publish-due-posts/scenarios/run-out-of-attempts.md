---
kind: edge
routes:
  web: Web
steps:
  - text: A delivery that keeps failing temporarily fails its fifth attempt
    kind: condition
    unattended: true
    entities:
      - { entity: delivery, effect: reads, facts: [Attempts] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product stops retrying and leaves it failed with the last reason
    kind: product
    entities:
      - { entity: delivery, effect: changes, from: Retrying, to: Failed, facts: [Error] }
      - { entity: post, effect: changes, from: Scheduled, to: Failed, facts: [] }
    contexts: { web: { place: web::app::posts } }
---

# Run out of attempts

## Trigger

A platform stays down for hours.

## Outcome

The post is in Posts, Failed, waiting for a manual retry.
