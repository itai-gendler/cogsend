---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin publishes a post to several accounts
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Selected accounts] }
      - { entity: account, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product queues and sends a delivery for each account
    kind: product
    actor: admin
    entities:
      - { entity: delivery, as: accepted, effect: creates, to: Queued, facts: [Attempts] }
      - { entity: delivery, as: refused, effect: creates, to: Queued, facts: [Attempts] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: One platform accepts the post and another refuses it for good
    kind: product
    actor: admin
    entities:
      - { entity: delivery, as: accepted, effect: changes, from: Queued, to: Published, facts: [Link] }
      - { entity: delivery, as: refused, effect: changes, from: Queued, to: Failed, facts: [Error, Attempts] }
      - { entity: post, effect: changes, from: Draft, to: Partly published, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: "The composer keeps the post open, says Couldn't publish everywhere and lists why"
    kind: condition
    entities:
      - { entity: delivery, as: refused, effect: reads, facts: [Error] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Some accounts fail

## Trigger

One platform refuses the post, for its length or an expired token.

## Outcome

The post is published where it could be, and the failure waits in Posts, Failed with a Retry.

## Edge cases

- A refusal that means the account's credentials stopped working marks the account Needs reconnect.
- A temporary failure such as a rate limit retries on its own instead of failing.
- A post that failed on some accounts stays editable so it can be fixed and retried.
