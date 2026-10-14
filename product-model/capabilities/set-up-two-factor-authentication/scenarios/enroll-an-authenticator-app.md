---
kind: primary
routes:
  web: Web
steps:
  - text: The Product shows a new authenticator QR code, its key and ten backup codes
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: reads, facts: [Authenticator, Backup codes] }
    contexts: { web: { place: web::login::set-up-authenticator } }
  - text: The Admin scans the code, saves the backup codes and enters the first code from the app
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::set-up-authenticator } }
  - text: The Product checks the code, keeps the authenticator and backup codes on the Admin and signs them in
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: changes, from: Awaiting two-factor setup, to: Two-factor active, facts: [Authenticator, Backup codes] }
    contexts: { web: { place: web::login::set-up-authenticator } }
---

# Enroll an authenticator app

## Trigger

The Admin's password was accepted and no authenticator is enrolled yet.

## Outcome

Two-factor authentication is active and the Admin is in the app.
