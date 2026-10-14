---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks to duplicate a post
    kind: actor
    actor: api-client
    entities:
      - { entity: post, as: original, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product creates a Draft copy and returns it
    kind: product
    actor: api-client
    entities:
      - { entity: post, as: copy, effect: creates, to: Draft, facts: [Title, Text, Selected accounts, Last edited] }
    contexts: { api: { place: api } }
---

# Duplicate through the API

## Trigger

A script reposts something that went out everywhere.

## Outcome

A new draft copy exists.
