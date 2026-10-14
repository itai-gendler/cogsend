---
kind: validation
routes:
  api: API
steps:
  - text: The API client sends new text for a post
    kind: actor
    actor: api-client
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: Every delivery of the post is published, so the Product refuses with Already published, duplicate it to post again
    kind: condition
    entities:
      - { entity: post, effect: reads, facts: [] }
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Edit a post published everywhere

## Trigger

A script tries to change a post that already went out.

## Outcome

The post is unchanged; a copy is the way to post it again.

## Edge cases

- While any delivery is being sent the Product refuses with Publishing in progress instead, and the composer pauses editing until the result is in.
