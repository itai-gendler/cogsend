---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin removes an image from a card
    kind: actor
    actor: admin
    entities:
      - { entity: image, effect: reads, facts: [Card] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product deletes the image and its file
    kind: product
    actor: admin
    entities:
      - { entity: image, effect: removes }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Remove an image from a card

## Trigger

The wrong picture was attached.

## Outcome

The card no longer has the image.
