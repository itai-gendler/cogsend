---
kind: validation
result: not-achieved
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
  - text: The Admin enters a code that is not valid
    kind: actor
    capability: enter-authenticator-code
    actor: admin
    entities: []
    contexts: { web: { place: web::login::enter-code } }
  - text: The Product answers Invalid code and keeps the Admin signed out
    kind: condition
    capability: enter-authenticator-code
    entities:
      - { entity: admin, effect: reads, facts: [Authenticator] }
    contexts: { web: { place: web::login::enter-code } }
---

# Enter a wrong code

## Trigger

The Admin mistypes the code.

## Outcome

The Admin is still signed out.
