---
kind: primary
routes:
  api: API
steps:
  - text: The API client sends a title and text for a new draft
    kind: actor
    actor: api-client
    entities: []
    contexts: { api: { place: api } }
  - text: The Product creates a Draft post with them and returns it
    kind: product
    actor: api-client
    entities:
      - { entity: post, effect: creates, to: Draft, facts: [Title, Text, Last edited] }
    contexts: { api: { place: api } }
---

# Create a draft through the API

## Trigger

A script wants to prepare a post.

## Outcome

A Draft post exists that the script can schedule or publish.

## Edge cases

- Text over 100,000 characters is refused.
