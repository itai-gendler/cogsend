---
kind: validation
routes:
  api: API
steps:
  - text: The API client asks to schedule a draft for an account it already published to, or is publishing to
    kind: actor
    actor: api-client
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product refuses with Already published or Already publishing and names the accounts
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [] }
      - { entity: post, effect: reads, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Schedule an account that already has the post

## Trigger

A script schedules a post that partly went out.

## Outcome

No account is scheduled to get the post twice.
