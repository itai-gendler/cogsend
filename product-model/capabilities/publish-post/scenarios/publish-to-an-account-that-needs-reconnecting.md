---
kind: validation
routes:
  api: API
steps:
  - text: The API client asks to publish a draft to an account that needs reconnecting
    kind: actor
    actor: api-client
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product sends nothing and answers that one or more accounts were not found
    kind: condition
    entities:
      - { entity: post, effect: reads, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Publish to an account that needs reconnecting

## Trigger

A script publishes to an account whose token expired.

## Outcome

Nothing is sent until the account is reconnected.
