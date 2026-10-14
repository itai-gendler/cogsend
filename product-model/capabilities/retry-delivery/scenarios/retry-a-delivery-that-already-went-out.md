---
kind: edge
routes:
  api: API
steps:
  - text: The API client asks to retry a delivery that is already published
    kind: actor
    actor: api-client
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product sends nothing and answers that it is published and was skipped
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [Link] }
    contexts: { api: { place: api } }
---

# Retry a delivery that already went out

## Trigger

A script retries twice.

## Outcome

The account does not get the post twice.
