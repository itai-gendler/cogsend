---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks to delete an image of a post
    kind: actor
    actor: api-client
    entities:
      - { entity: image, effect: reads, facts: [] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product deletes the image and its file
    kind: product
    actor: api-client
    entities:
      - { entity: image, effect: removes }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Delete an image through the API

## Trigger

A script removes an attachment.

## Outcome

The image is gone.
