---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin enters a code that is neither current nor an unused backup code
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product answers Invalid code and keeps the current authenticator
    kind: condition
    entities:
      - { entity: admin, effect: reads, facts: [Authenticator, Backup codes] }
    contexts: { web: { place: web::app::settings } }
---

# Prove the current authenticator wrongly

## Trigger

Someone at an unlocked session tries to take over the second factor.

## Outcome

Nothing changes.
