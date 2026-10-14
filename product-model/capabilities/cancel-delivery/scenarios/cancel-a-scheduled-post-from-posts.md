---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Cancel on a scheduled card
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text] }
      - { entity: delivery, effect: reads, facts: [Scheduled time] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product cancels each of its waiting deliveries and the post becomes a draft again
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: changes, from: Scheduled, to: Cancelled, facts: [] }
      - { entity: post, effect: changes, from: Scheduled, to: Draft, facts: [] }
    contexts: { web: { place: web::app::posts } }
---

# Cancel a scheduled post from Posts

## Trigger

A scheduled post should not go out.

## Outcome

Nothing is published and the post is back in Drafts.
