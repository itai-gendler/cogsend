---
kind: primary
result: achieved
routes:
  web: Web
steps:
  - text: The Admin enters their email and password
    kind: actor
    capability: sign-in
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product accepts them and asks for an authenticator code
    kind: product
    capability: sign-in
    actor: admin
    entities:
      - { entity: admin, effect: reads, facts: [Email, Password] }
    contexts: { web: { place: web::login::enter-code } }
  - text: The Admin enters the code from their authenticator app
    kind: actor
    capability: enter-authenticator-code
    actor: admin
    entities: []
    contexts: { web: { place: web::login::enter-code } }
  - text: The Product accepts it and signs the Admin in
    kind: product
    capability: enter-authenticator-code
    actor: admin
    entities:
      - { entity: admin, effect: reads, facts: [Authenticator] }
    contexts: { web: { place: web::login::enter-code } }
---

# Sign in and enter a code

## Trigger

The Admin opens the instance while signed out.

## Outcome

The Admin is in the app.
