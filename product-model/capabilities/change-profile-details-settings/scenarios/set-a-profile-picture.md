---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin edits the profile picture, enters a picture address and saves
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: "The Product keeps the picture and shows it on the Admin's avatar"
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: changes, facts: [Profile picture] }
    contexts: { web: { place: web::app::settings } }
---

# Set a profile picture

## Trigger

The Admin wants a picture on their avatar.

## Outcome

The avatar shows the picture.
