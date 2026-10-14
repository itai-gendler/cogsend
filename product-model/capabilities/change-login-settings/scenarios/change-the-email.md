---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin enters a new email and their current password and presses Save login
    kind: actor
    actor: admin
    entities:
      - { entity: admin, effect: reads, facts: [Email] }
    contexts: { web: { place: web::app::settings } }
  - text: The Product checks the password and saves the new email
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: changes, facts: [Email] }
    contexts: { web: { place: web::app::settings } }
---

# Change the email

## Trigger

The Admin moves to another address.

## Outcome

The Admin signs in with the new email from now on.
