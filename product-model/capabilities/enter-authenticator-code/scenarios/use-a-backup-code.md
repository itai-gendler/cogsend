---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin chooses to use a backup code and enters one they saved
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::enter-code } }
  - text: The Product accepts the unused backup code, marks it used and signs the Admin in
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: changes, facts: [Backup codes] }
    contexts: { web: { place: web::login::enter-code } }
---

# Use a backup code

## Trigger

The Admin does not have their authenticator app at hand.

## Outcome

The Admin is signed in and that backup code can never be used again.
