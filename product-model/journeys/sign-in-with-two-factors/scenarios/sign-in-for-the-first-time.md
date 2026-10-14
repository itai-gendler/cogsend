---
kind: alternative
result: achieved
routes:
  web: Web
steps:
  - text: The Admin enters the email and password the operator set up
    kind: actor
    capability: sign-in
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product accepts them and, with no authenticator enrolled, sends the Admin to set one up
    kind: product
    capability: sign-in
    actor: admin
    entities:
      - { entity: admin, effect: reads, facts: [Email, Password] }
    contexts: { web: { place: web::login::set-up-authenticator } }
  - text: The Admin scans the QR code, saves the backup codes and enters the first code
    kind: actor
    capability: set-up-two-factor-authentication
    actor: admin
    entities: []
    contexts: { web: { place: web::login::set-up-authenticator } }
  - text: The Product enrolls the authenticator and signs the Admin in
    kind: product
    capability: set-up-two-factor-authentication
    actor: admin
    entities:
      - { entity: admin, effect: changes, from: Awaiting two-factor setup, to: Two-factor active, facts: [Authenticator, Backup codes] }
    contexts: { web: { place: web::login::set-up-authenticator } }
---

# Sign in for the first time

## Trigger

The operator created the account from a terminal, so no authenticator exists yet.

## Outcome

The Admin is in the app with two-factor authentication on.
