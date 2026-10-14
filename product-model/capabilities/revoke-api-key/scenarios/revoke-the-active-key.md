---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Revoke on the active key and confirms
    kind: actor
    actor: admin
    entities:
      - { entity: api-key, effect: reads, facts: [Prefix] }
    contexts: { web: { place: web::app::settings } }
  - text: The Product revokes it and shows that there is no active key
    kind: product
    actor: admin
    entities:
      - { entity: api-key, effect: changes, from: Active, to: Revoked, facts: [] }
    contexts: { web: { place: web::app::settings } }
---

# Revoke the active key

## Trigger

The Admin no longer wants anything to call the API.

## Outcome

No key is accepted.
