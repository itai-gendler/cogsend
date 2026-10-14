---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks to delete a draft
    kind: actor
    actor: api-client
    entities: []
    contexts: { api: { place: api } }
  - text: The Product deletes the post with its images and overrides
    kind: product
    actor: api-client
    entities:
      - { entity: post, effect: removes, from: Draft }
      - { entity: image, effect: removes, with: post }
      - { entity: platform-override, effect: removes, with: post }
    contexts: { api: { place: api } }
---

# Delete through the API

## Trigger

A script cleans up drafts it created.

## Outcome

The draft is gone.
