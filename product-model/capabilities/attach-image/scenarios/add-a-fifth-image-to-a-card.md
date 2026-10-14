---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin adds an image to a card that already has four
    kind: actor
    actor: admin
    entities:
      - { entity: image, effect: reads, facts: [Card] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product refuses with Max 4 images per post
    kind: condition
    entities:
      - { entity: post, effect: reads, facts: [] }
      - { entity: image, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Add a fifth image to a card

## Trigger

The Admin tries to put more images on one card than platforms take.

## Outcome

The card keeps its four images; another card can take more.

## Edge cases

- A post holds at most 32 files across its cards, and the Admin at most 1,000 files in all.
