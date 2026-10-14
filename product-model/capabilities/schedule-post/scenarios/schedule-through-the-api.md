---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks to schedule a draft for one or more accounts at a time
    kind: actor
    actor: api-client
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: "The Product schedules a delivery for each named account and leaves the post's other deliveries as they are"
    kind: product
    actor: api-client
    entities:
      - { entity: delivery, effect: creates, to: Scheduled, facts: [Scheduled time, Attempts] }
      - { entity: post, effect: changes, from: Draft, to: Scheduled, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Schedule through the API

## Trigger

A script queues a post for later.

## Outcome

The post waits for its time on those accounts.

## Decision points

### Other accounts

Did the script ask to cancel the others?

- No → the post's other waiting deliveries keep their times
- Yes → the post's other deliveries that are still waiting are cancelled and named in the answer
