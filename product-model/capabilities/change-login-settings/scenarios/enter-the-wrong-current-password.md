---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin enters a wrong current password and presses Save login
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product refuses with Current password is incorrect and counts the failure like a sign-in
    kind: condition
    entities:
      - { entity: admin, effect: reads, facts: [Password] }
    contexts: { web: { place: web::app::settings } }
---

# Enter the wrong current password

## Trigger

Someone at an unlocked session tries to take over the login.

## Outcome

Nothing changes.
