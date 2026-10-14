---
kind: primary
result: achieved
routes:
  web: Web
steps:
  - text: The Admin presses Quote on X on a post that published to X
    kind: actor
    capability: quote-x-post
    actor: admin
    entities:
      - { entity: delivery, effect: reads, facts: [Link] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
  - text: "The Product creates a new Draft post whose text is the X post's link and opens it in the composer"
    kind: product
    capability: quote-x-post
    actor: admin
    entities:
      - { entity: post, effect: creates, to: Draft, facts: [Text, Selected accounts, Last edited] }
      - { entity: account, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::composer } }
  - text: The Admin writes their comment above the quote
    kind: actor
    capability: edit-post
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product saves the post
    kind: product
    capability: edit-post
    actor: admin
    entities:
      - { entity: post, effect: changes, facts: [Text, Last edited] }
    contexts: { web: { place: web::app::composer } }
---

# Quote from Posts and add a comment

## Trigger

The Admin wants to add to something they posted on X.

## Outcome

The quote post is saved with the comment, ready to publish.
