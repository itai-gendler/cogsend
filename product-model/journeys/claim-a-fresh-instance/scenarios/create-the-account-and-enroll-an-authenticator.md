---
kind: primary
result: achieved
routes:
  web: Web
steps:
  - text: "The Admin enters the deployment's encryption key, an email and a password on the login page"
    kind: actor
    capability: create-admin-account
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product creates the Admin and sends them to set up an authenticator
    kind: product
    capability: create-admin-account
    actor: admin
    entities:
      - { entity: admin, effect: creates, to: Awaiting two-factor setup, facts: [Email, Password, Time zone] }
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

# Create the account and enroll an authenticator

## Trigger

An instance deployed with the button opens for the first time.

## Outcome

The instance is claimed and protected by two factors.
