---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin enters a profile picture address that is not https
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product refuses it and keeps the current picture
    kind: condition
    entities:
      - { entity: admin, effect: reads, facts: [Profile picture] }
    contexts: { web: { place: web::app::settings } }
---

# Use a picture address that is not https

## Trigger

The Admin pastes an http link.

## Outcome

The picture is unchanged.
