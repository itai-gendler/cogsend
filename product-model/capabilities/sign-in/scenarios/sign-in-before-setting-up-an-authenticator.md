---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin enters their email and password
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The password is right but the Admin is still awaiting two-factor setup
    kind: condition
    entities:
      - { entity: admin, effect: reads, facts: [Email, Password] }
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product sends the Admin to set up an authenticator
    kind: product
    actor: admin
    entities: []
    contexts: { web: { place: web::login::set-up-authenticator } }
---

# Sign in before setting up an authenticator

## Trigger

The Admin signs in for the first time, or after the operator cleared their
authenticator from the deployment.

## Outcome

The Admin is setting up an authenticator before they can get in.
