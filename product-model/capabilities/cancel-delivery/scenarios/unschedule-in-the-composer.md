---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin opens a scheduled post and presses Unschedule
    kind: actor
    actor: admin
    entities:
      - { entity: delivery, effect: reads, facts: [Scheduled time] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product cancels its waiting deliveries and says it is a draft again
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: changes, from: Scheduled, to: Cancelled, facts: [] }
      - { entity: post, effect: changes, from: Scheduled, to: Draft, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Unschedule in the composer

## Trigger

The Admin wants to keep working on a scheduled post without a deadline.

## Outcome

The post is a draft again.

## Edge cases

- An account whose delivery is already being sent cannot be unscheduled, and the composer names it.
