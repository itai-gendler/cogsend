---
kind: edge
routes:
  web: Web
steps:
  - text: "A due delivery is sent and the platform refuses it for a reason retrying cannot change, such as its credentials or the text's length"
    kind: condition
    unattended: true
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product fails it at once with the reason, and marks the account as needing reconnection when its credentials were refused
    kind: product
    entities:
      - { entity: delivery, effect: changes, from: Scheduled, to: Failed, facts: [Error, Attempts] }
      - { entity: post, effect: changes, from: Scheduled, to: Failed, facts: [] }
      - { entity: account, effect: changes, from: Active, to: Needs reconnect, facts: [] }
    contexts: { web: { place: web::app::posts } }
---

# A platform refuses for good

## Trigger

An account's token expired before its scheduled post.

## Outcome

The post is failed with the reason, and the account is marked for reconnecting.

## Edge cases

- On X, LinkedIn and Threads, a request that got no answer fails saying the post may have been published, and is never retried on its own.
- A delivery whose account cannot refresh its token is failed without spending an attempt.
