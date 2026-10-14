---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin enters their email and password
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product checks them against the Admin's email and password
    kind: condition
    entities:
      - { entity: admin, effect: reads, facts: [Email, Password] }
    contexts: { web: { place: web::login::sign-in } }
  - text: The Admin has an authenticator, so the Product asks for a code from it
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: reads, facts: [] }
    contexts: { web: { place: web::login::enter-code } }
---

# Sign in with email and password

## Trigger

The Admin opens the instance while signed out.

## Outcome

The password is accepted and the Admin is asked for an authenticator code.
