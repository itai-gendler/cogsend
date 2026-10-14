---
kind: primary
routes:
  api: API
steps:
  - text: The API client sends alt text for an image of a post
    kind: actor
    actor: api-client
    entities:
      - { entity: image, effect: reads, facts: [] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product saves it on the image
    kind: product
    actor: api-client
    entities:
      - { entity: image, effect: changes, facts: [Alt text] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Set alt text through the API

## Trigger

A script describes an uploaded image.

## Outcome

The image carries its alt text.
