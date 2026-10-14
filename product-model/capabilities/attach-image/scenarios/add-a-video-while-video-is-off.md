---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin adds a video to a card
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: The Instance has video uploads off, so the Product refuses with Video uploads are not enabled on this instance
    kind: condition
    entities:
      - { entity: instance, effect: reads, facts: [Video uploads] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Add a video while video is off

## Trigger

The Admin tries to post a video on an instance that does not take them.

## Outcome

No video is attached.
