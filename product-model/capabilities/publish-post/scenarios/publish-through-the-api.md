---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks to publish a draft to one account
    kind: actor
    actor: api-client
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product queues a delivery for that account and sends the post
    kind: product
    actor: api-client
    entities:
      - { entity: delivery, effect: creates, to: Queued, facts: [Attempts] }
      - { entity: post, effect: reads, facts: [Text] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The platform accepts it and the Product answers with the result and the link
    kind: product
    actor: api-client
    entities:
      - { entity: delivery, effect: changes, from: Queued, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Draft, to: Published, facts: [] }
    contexts: { api: { place: api } }
---

# Publish through the API

## Trigger

A script publishes a post it prepared.

## Outcome

The post is published on that account.

## Edge cases

- A request names at most ten accounts.
