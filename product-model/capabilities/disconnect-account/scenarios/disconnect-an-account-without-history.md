---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin disconnects an account that never published anything and confirms
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Handle] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Product removes the account with its unpublished deliveries
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: removes, from: Active }
      - { entity: delivery, effect: removes, from: Scheduled, with: account }
    contexts: { web: { place: web::app::accounts } }
---

# Disconnect an account without history

## Trigger

The Admin connected the wrong account.

## Outcome

The account is gone.
