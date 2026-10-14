---
kind: primary
routes:
  api: API
steps:
  - text: The API client uploads an image for one card of a post, with its alt text
    kind: actor
    actor: api-client
    entities:
      - { entity: image, effect: reads, facts: [] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product checks its format and size and stores it on that card
    kind: product
    actor: api-client
    entities:
      - { entity: image, effect: creates, facts: [Card, Order, Alt text, Format, Size, Dimensions] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Upload an image through the API

## Trigger

A script attaches a picture to a prepared post.

## Outcome

The image is on the card.
