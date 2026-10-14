---
kind: edge
routes:
  web: Web
steps:
  - text: The Admin takes longer than the approval allows, or declines on the platform
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product returns the Admin to Accounts with the reason and connects nothing
    kind: condition
    entities:
      - { entity: account, effect: reads, facts: [] }
      - { entity: admin, effect: reads, facts: [] }
    contexts: { web: { place: web::app::accounts } }
---

# Approval expires or is refused

## Trigger

The platform's approval page was left open or declined.

## Outcome

Nothing is connected; the Admin can start again.
