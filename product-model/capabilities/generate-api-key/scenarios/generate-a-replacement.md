---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin presses Generate replacement on the active key and confirms
    kind: actor
    actor: admin
    entities:
      - { entity: api-key, as: old, effect: reads, facts: [Prefix] }
    contexts: { web: { place: web::app::settings } }
  - text: The Product revokes the old key and creates a new active one, shown once
    kind: product
    actor: admin
    entities:
      - { entity: api-key, as: old, effect: changes, from: Active, to: Revoked, facts: [] }
      - { entity: api-key, as: new, effect: creates, to: Active, facts: [Prefix, Scope, Created] }
    contexts: { web: { place: web::app::settings } }
---

# Generate a replacement

## Trigger

A key may have leaked, or its scope should change.

## Outcome

Only the new key works.
