---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin opens a scheduled post, unticks one of its accounts and presses Publish now
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Selected accounts] }
      - { entity: delivery, as: kept, effect: reads, facts: [Scheduled time] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product sends the post now to the accounts still ticked and unschedules the unticked one
    kind: product
    actor: admin
    entities:
      - { entity: delivery, as: kept, effect: changes, from: Scheduled, to: Published, facts: [Link] }
      - { entity: delivery, as: dropped, effect: changes, from: Scheduled, to: Cancelled, facts: [] }
      - { entity: post, effect: changes, from: Scheduled, to: Published, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Publish a scheduled post now

## Trigger

The Admin decides not to wait for the scheduled time.

## Outcome

The post is out now on the ticked accounts and will not post later on the unticked one.
