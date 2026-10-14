---
kind: primary
routes:
  api: API
steps:
  - text: The API client sends new text for a draft
    kind: actor
    actor: api-client
    entities: []
    contexts: { api: { place: api } }
  - text: The Product saves the post
    kind: product
    actor: api-client
    entities:
      - { entity: post, effect: changes, facts: [Text, Last edited] }
    contexts: { api: { place: api } }
---

# Edit a draft through the API

## Trigger

A script updates a prepared post.

## Outcome

The post holds the new text.
