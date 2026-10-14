---
kind: edge
routes:
  web: Web
steps:
  - text: The Admin publishes a post again to an account it already went out on
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [] }
      - { entity: account, effect: reads, facts: [Handle] }
    contexts: { web: { place: web::app::composer } }
  - text: The delivery is already published, so the Product sends nothing to that account and says so
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [Link] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Publish again to an account that has it

## Trigger

The Admin presses Publish twice, or republishes a partly published post.

## Outcome

No account receives the post twice.
