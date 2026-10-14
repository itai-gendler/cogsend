---
kind: edge
routes:
  api: API
steps:
  - text: The API client asks to publish a draft to several accounts at once
    kind: actor
    actor: api-client
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: "The Product sends the first delivery and every further one that fits in the Instance's call budget"
    kind: product
    actor: api-client
    entities:
      - { entity: delivery, effect: creates, to: Queued, facts: [Attempts] }
      - { entity: instance, effect: reads, facts: [Call budget] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The deliveries that do not fit stay queued and are answered as deferred, for the next tick to send
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Publish to more accounts than one request affords

## Trigger

A script publishes to many accounts on the Workers free plan.

## Outcome

Every delivery goes out, some on the next tick, and none twice.

## Edge cases

- A request that runs out part-way answers with what it did get; the deliveries it did not complete stay due.
