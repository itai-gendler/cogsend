---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin enters a code that is neither current nor an unused backup code
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::enter-code } }
  - text: The Product answers Invalid code and keeps the Admin signed out
    kind: condition
    entities:
      - { entity: admin, effect: reads, facts: [Authenticator, Backup codes] }
    contexts: { web: { place: web::login::enter-code } }
---

# Enter an invalid code

## Trigger

The Admin mistypes the code or enters an expired one.

## Outcome

The Admin stays signed out and can try again.

## Edge cases

- After eight wrong codes the Admin is sent back to sign in again, and codes are refused for fifteen minutes.
