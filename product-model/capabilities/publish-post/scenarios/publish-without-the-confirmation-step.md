---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin earlier ticked Publish without asking next time, and now presses Publish
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text, Selected accounts] }
      - { entity: account, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product queues a delivery for each ticked account and sends the post at once
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: creates, to: Queued, facts: [Attempts] }
      - { entity: account, effect: reads, facts: [] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product sends the post and records each result
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: changes, from: Queued, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Draft, to: Published, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Publish without the confirmation step

## Trigger

The Admin publishes often and turned the question off in this browser.

## Outcome

The post is published without the extra step.

## Edge cases

- Settings, Preferences, Ask for confirmation before publishing turns the question back on.
