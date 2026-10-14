---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Reschedule on a scheduled card and picks an offset or a specific time
    kind: actor
    actor: admin
    entities:
      - { entity: delivery, effect: reads, facts: [Scheduled time] }
    contexts: { web: { place: web::app::posts } }
  - text: "The Product moves each of the card's waiting deliveries to that time"
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: changes, facts: [Scheduled time, Attempts] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
---

# Reschedule from Posts

## Trigger

A scheduled post should go out at another time.

## Outcome

The post waits for its new time.
