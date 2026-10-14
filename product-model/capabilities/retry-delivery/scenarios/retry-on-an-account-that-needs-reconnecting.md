---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin presses Retry on a delivery whose account needs reconnecting
    kind: actor
    actor: admin
    entities:
      - { entity: delivery, effect: reads, facts: [Error] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product refuses with Account needs reconnect
    kind: condition
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
---

# Retry on an account that needs reconnecting

## Trigger

A post failed because the account's token expired.

## Outcome

Nothing is sent until the account is reconnected.
