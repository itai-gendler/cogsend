---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks for the drafts, or for the publish queue
    kind: actor
    actor: api-client
    entities: []
    contexts: { api: { place: api } }
  - text: The Product answers with the posts and their deliveries
    kind: product
    actor: api-client
    entities:
      - { entity: post, effect: reads, facts: [Title, Text, Last edited] }
      - { entity: delivery, effect: reads, facts: [Scheduled time, Error, Link] }
    contexts: { api: { place: api } }
---

# List drafts and the queue through the API

## Trigger

A script checks what is waiting to go out.

## Outcome

The script has the posts and each delivery's state.

## Edge cases

- The drafts list returns 200 posts and the queue 100 deliveries by default, at most 500 either way.
