---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin enters a code that does not match the new authenticator
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::set-up-authenticator } }
  - text: The Product answers Invalid code and keeps the Admin awaiting two-factor setup
    kind: condition
    entities:
      - { entity: admin, effect: reads, facts: [Authenticator] }
    contexts: { web: { place: web::login::set-up-authenticator } }
---

# Confirm with a wrong code

## Trigger

The Admin types a code before the app has the key, or mistypes it.

## Outcome

Nothing is enrolled; the Admin can try again with the next code.

## Edge cases

- Setup expires after ten minutes; the Admin then signs in again.
