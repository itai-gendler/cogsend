---
kind: alternative
routes:
  web: Web
steps:
  - text: "The Admin opens the quote button in a card's tools"
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: "The Product lists the Admin's recent published X posts"
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: reads, facts: [Link] }
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::composer } }
  - text: The Admin picks one and the Product adds its link at the end of the card
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: changes, facts: [Text, Last edited] }
    contexts: { web: { place: web::app::composer } }
---

# Pick one of your recent X posts

## Trigger

The Admin wants to quote something they posted earlier.

## Outcome

The card quotes that earlier post.
