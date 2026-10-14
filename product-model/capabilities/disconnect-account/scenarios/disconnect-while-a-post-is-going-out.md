---
kind: edge
routes:
  web: Web
steps:
  - text: The Admin disconnects an account
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Handle] }
    contexts: { web: { place: web::app::accounts } }
  - text: One of its deliveries is being sent, so the Product refuses with Publishing in progress, try again shortly, and keeps the account
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::accounts } }
---

# Disconnect while a post is going out

## Trigger

The Admin disconnects in the seconds a post is going out to it.

## Outcome

The account stays connected until the delivery settles.
