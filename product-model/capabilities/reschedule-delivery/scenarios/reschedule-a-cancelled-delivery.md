---
kind: validation
routes:
  api: API
steps:
  - text: The API client asks to reschedule a cancelled delivery
    kind: actor
    actor: api-client
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product refuses with Cancelled, retry instead
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Reschedule a cancelled delivery

## Trigger

A script reschedules something that was cancelled.

## Outcome

Nothing changes; a retry is the way back.

## Edge cases

- A delivery whose account needs reconnecting is refused with Account needs reconnect.
- A time in the past or more than a year ahead is refused.
