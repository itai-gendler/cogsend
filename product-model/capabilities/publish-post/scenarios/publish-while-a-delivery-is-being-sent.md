---
kind: edge
routes:
  api: API
steps:
  - text: The API client asks to publish a draft to an account it is already being sent to
    kind: actor
    actor: api-client
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: That delivery is publishing, so the Product refuses with Already publishing and names the account
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [] }
      - { entity: post, effect: reads, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Publish while a delivery is being sent

## Trigger

A script retries a publish before the first one finished.

## Outcome

Nothing is sent twice; the script waits and tries again.
