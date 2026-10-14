---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin enters the six-digit code their authenticator app shows
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::enter-code } }
  - text: The Product checks the code against the Admin's authenticator and signs them in
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: reads, facts: [Authenticator] }
    contexts: { web: { place: web::login::enter-code } }
---

# Enter a code from the app

## Trigger

The Admin's password was accepted.

## Outcome

The Admin is signed in and on the dashboard.

## Edge cases

- A code already used once is not accepted again.
