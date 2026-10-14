---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin opens Settings, Scheduled publishing
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product shows when the last tick arrived and, when ticks are missing or late, what to do about it
    kind: product
    actor: admin
    entities:
      - { entity: instance, effect: reads, facts: [Last tick] }
    contexts: { web: { place: web::app::settings } }
---

# Check scheduled publishing in Settings

## Trigger

Scheduled posts are not going out.

## Outcome

The Admin knows whether ticks arrive and what to set up if not.

## Edge cases

- No tick yet is normal for the first few minutes of a fresh deployment.
