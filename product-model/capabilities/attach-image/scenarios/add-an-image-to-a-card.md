---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin adds an image to a card
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text] }
      - { entity: image, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product shrinks an image over 2 MB to 2560 pixels on its long edge in the browser and stores the image on that card
    kind: product
    actor: admin
    entities:
      - { entity: image, effect: creates, facts: [Card, Order, Format, Size, Dimensions] }
    contexts: { web: { place: web::app::composer } }
---

# Add an image to a card

## Trigger

A card needs a picture.

## Outcome

The image is on the card, ready for its alt text.

## Edge cases

- GIFs and animated WebP are not shrunk, so their animation survives.
- Platform size and format limits are checked again when the post is published.
