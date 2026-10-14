---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Check on an account that needs reconnecting
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform, Handle] }
    contexts: { web: { place: web::app::accounts } }
  - text: The platform accepts its credentials, so the Product marks it active and says Account is active again
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: changes, from: Needs reconnect, to: Active, facts: [Credentials] }
    contexts: { web: { place: web::app::accounts } }
---

# Check an account that works again

## Trigger

The Admin fixed the account on the platform's side, or reconnected it in Zernio.

## Outcome

The account is active and receives posts again.
