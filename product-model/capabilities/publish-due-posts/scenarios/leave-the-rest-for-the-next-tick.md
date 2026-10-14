---
kind: edge
routes:
  web: Web
steps:
  - text: A tick finds more due deliveries than its call budget can publish
    kind: condition
    unattended: true
    entities:
      - { entity: delivery, effect: reads, facts: [Scheduled time] }
      - { entity: instance, effect: reads, facts: [Call budget] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product publishes the oldest and each further one whose estimated calls still fit, and leaves the rest due
    kind: product
    entities:
      - { entity: delivery, effect: changes, from: Scheduled, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Scheduled, to: Published, facts: [] }
    contexts: { web: { place: web::app::posts } }
---

# Leave the rest for the next tick

## Trigger

A backlog builds up on the Workers free plan.

## Outcome

The backlog drains a post or two a minute, and no post is cut off half-way and sent twice.
