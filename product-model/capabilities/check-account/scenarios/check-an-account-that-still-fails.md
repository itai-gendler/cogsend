---
kind: edge
routes:
  web: Web
steps:
  - text: The Admin presses Check on an account
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Handle] }
    contexts: { web: { place: web::app::accounts } }
  - text: The platform refuses its credentials, so the Product marks it as needing reconnection
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: changes, from: Active, to: Needs reconnect, facts: [] }
    contexts: { web: { place: web::app::accounts } }
---

# Check an account that still fails

## Trigger

The Admin suspects an account stopped working.

## Outcome

The account is marked, and Reconnect is the way back.
