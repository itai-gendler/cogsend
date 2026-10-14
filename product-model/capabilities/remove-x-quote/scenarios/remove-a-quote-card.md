---
kind: primary
routes:
  web: Web
steps:
  - text: "The Admin presses × on a card's quote card"
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: "The Product takes the quoted link off the end of the card's text"
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: changes, facts: [Text, Last edited] }
    contexts: { web: { place: web::app::composer } }
---

# Remove a quote card

## Trigger

The quote is no longer wanted.

## Outcome

The card no longer quotes anything.
