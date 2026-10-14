---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin opens a scheduled post and presses Change time
    kind: actor
    actor: admin
    entities:
      - { entity: delivery, effect: reads, facts: [Scheduled time] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The Admin picks a new time
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: "The Product moves the post's waiting deliveries to the new time"
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: changes, facts: [Scheduled time] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Change the time of a scheduled post

## Trigger

Plans change.

## Outcome

The post goes out at the new time.
