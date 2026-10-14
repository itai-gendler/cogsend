---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Publish on a post
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text, Selected accounts] }
      - { entity: account, effect: reads, facts: [Platform, Handle] }
    contexts: { web: { place: web::app::composer } }
  - text: The Admin confirms the Confirm Post step
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product queues a delivery for each ticked account
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: creates, to: Queued, facts: [Attempts] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product sends the post to each account in turn
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: changes, from: Queued, to: Publishing, facts: [] }
      - { entity: account, effect: reads, facts: [Credentials] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: Each platform accepts it and the Product records where it landed
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: changes, from: Publishing, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Draft, to: Published, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The composer shows the result for each account and empties for the next post, linking to it in Posts
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [Link] }
      - { entity: post, effect: reads, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Publish to every ticked account

## Trigger

A draft is ready to go out now.

## Outcome

The post is published on every ticked account, with a link to each.

## Edge cases

- LinkedIn has no threads: a thread sent there is flattened into one post.
- A post opened from Posts returns the Admin to Posts instead of a blank composer.
- Cmd or Ctrl with Enter publishes from the keyboard.
