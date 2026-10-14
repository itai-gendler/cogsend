---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks to retry a failed delivery
    kind: actor
    actor: api-client
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product sends it again and answers with the result
    kind: product
    actor: api-client
    entities:
      - { entity: delivery, effect: changes, from: Failed, to: Published, facts: [Error, Attempts, Link] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Retry through the API

## Trigger

A script retries after a platform outage.

## Outcome

The delivery is published.
