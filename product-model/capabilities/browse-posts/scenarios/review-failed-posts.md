---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin opens the Failed tab
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::posts } }
  - text: The Product lists each post with a failed delivery and the reason for each account that failed
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text] }
      - { entity: delivery, effect: reads, facts: [Error] }
      - { entity: account, effect: reads, facts: [Handle] }
    contexts: { web: { place: web::app::posts } }
---

# Review failed posts

## Trigger

The dashboard says posts failed to publish.

## Outcome

The Admin sees why each one failed and can retry it.

## Edge cases

- A post still retrying on its own is not failed yet and is not listed here.
