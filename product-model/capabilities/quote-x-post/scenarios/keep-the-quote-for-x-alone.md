---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin chooses Only on X on a quote card
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: The Product gives X its own tab carrying the quote and takes the link out of the Global text
    kind: product
    actor: admin
    entities:
      - { entity: platform-override, effect: creates, facts: [Platform, Text] }
      - { entity: post, effect: changes, facts: [Text, Last edited] }
    contexts: { web: { place: web::app::composer } }
---

# Keep the quote for X alone

## Trigger

The quote only makes sense on X.

## Outcome

X gets the quote and the other platforms get the text without the link.

## Edge cases

- Share with all on the X tab gives the other platforms the link again.
- A card holding only the quote cannot be split this way.
