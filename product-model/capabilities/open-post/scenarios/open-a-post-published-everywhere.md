---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin opens a post that went out to every account
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product shows it read-only with the result per account and offers Duplicate to post again
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text] }
      - { entity: delivery, effect: reads, facts: [Link] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Open a post published everywhere

## Trigger

The Admin looks back at a published post.

## Outcome

The Admin sees what went out and where, without being able to change it.
