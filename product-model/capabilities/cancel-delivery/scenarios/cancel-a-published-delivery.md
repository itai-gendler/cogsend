---
kind: validation
routes:
  api: API
steps:
  - text: The API client asks to cancel a delivery that already went out
    kind: actor
    actor: api-client
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product refuses with Already published
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [Link] }
    contexts: { api: { place: api } }
---

# Cancel a published delivery

## Trigger

A script cancels too late.

## Outcome

The published delivery stays published.

## Edge cases

- A delivery being sent right now is refused with Already publishing.
