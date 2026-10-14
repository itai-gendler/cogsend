---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin enters a display name under Profile Details and presses Save Changes
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product saves it and greets the Admin by it
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: changes, facts: [Display name] }
    contexts: { web: { place: web::app::settings } }
---

# Change the display name

## Trigger

The Admin wants the app to use their name.

## Outcome

The app greets the Admin by that name.

## Edge cases

- An empty name falls back to the first part of the email.
