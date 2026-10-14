---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin enters their current password and a new one twice and presses Save login
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product checks the current password, saves the new one and signs out every device, this one included
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: changes, facts: [Password] }
    contexts: { web: { place: web::app::settings } }
---

# Change the password

## Trigger

The Admin wants a new password.

## Outcome

Every device must sign in again with the new password.

## Edge cases

- A new password under eight characters, or the same as the current one, is refused.
- A Cloudflare token remembered for updates is forgotten with the old password.
