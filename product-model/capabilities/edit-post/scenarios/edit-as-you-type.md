---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin changes the text of a card in an open post
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product saves the post and the composer says Saved
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: changes, facts: [Text, Last edited] }
    contexts: { web: { place: web::app::composer } }
---

# Edit as you type

## Trigger

The Admin reworks a draft.

## Outcome

The post holds the new text.

## Edge cases

- A save that fails shows Not saved with Retry and is retried on its own until it goes through.
- Each card's counter uses the strictest character limit among the ticked accounts, counted the way that platform counts.
