---
kind: validation
routes:
  api: API
steps:
  - text: The API client asks to schedule a draft for a time in the past, or more than a year ahead
    kind: actor
    actor: api-client
    entities: []
    contexts: { api: { place: api } }
  - text: The Product refuses with runAt must be in the future, or must be within the next year
    kind: condition
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Schedule for a time that is not allowed

## Trigger

A script sends a stale or mistyped time.

## Outcome

Nothing is scheduled.
