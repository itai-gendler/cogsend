---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks to cancel one delivery
    kind: actor
    actor: api-client
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product cancels it
    kind: product
    actor: api-client
    entities:
      - { entity: delivery, effect: changes, from: Scheduled, to: Cancelled, facts: [] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Cancel a delivery through the API

## Trigger

A script takes one account off a schedule.

## Outcome

That account will not get the post.

## Edge cases

- A failed delivery can be cancelled too.
