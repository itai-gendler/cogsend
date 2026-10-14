---
kind: alternative
routes:
  api: API
steps:
  - text: The API client asks to reschedule a failed delivery to a new time
    kind: actor
    actor: api-client
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product schedules it at that time, clears its error and resets its attempts
    kind: product
    actor: api-client
    entities:
      - { entity: delivery, effect: changes, from: Failed, to: Scheduled, facts: [Scheduled time, Error, Attempts] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Reschedule a failed delivery through the API

## Trigger

A script tries a failed post again later instead of now.

## Outcome

The delivery waits for its new time.
