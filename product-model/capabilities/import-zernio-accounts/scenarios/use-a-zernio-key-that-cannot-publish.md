---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin pastes a Zernio key that is wrong, read-only or missing the publishing or accounts groups
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Product refuses with Zernio rejected this key, or this Zernio key cannot be used here, and imports nothing
    kind: condition
    entities: []
    contexts: { web: { place: web::app::accounts } }
---

# Use a Zernio key that cannot publish

## Trigger

The Admin created a Zernio key with too few permissions.

## Outcome

Nothing is imported until a usable key is given.
