---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Generate new authenticator and codes and enters a current authenticator or backup code
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product checks it and shows a new QR code, its key and ten new backup codes
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: reads, facts: [Authenticator, Backup codes] }
    contexts: { web: { place: web::app::settings } }
  - text: The Admin scans it, confirms they saved the new backup codes and enters a code from the new app
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product switches the Admin to the new authenticator and backup codes and signs out every other device
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: changes, facts: [Authenticator, Backup codes] }
    contexts: { web: { place: web::app::settings } }
---

# Move to a new authenticator

## Trigger

The Admin got a new phone or used up their backup codes.

## Outcome

Only the new authenticator and the new backup codes work.
