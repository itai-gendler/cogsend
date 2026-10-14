---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Remove on a draft card and confirms
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product hides it with an Undo for six seconds, then deletes it with its overrides and images
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: removes, from: Draft }
      - { entity: platform-override, effect: removes, with: post }
      - { entity: image, effect: removes, with: post }
    contexts: { web: { place: web::app::posts } }
---

# Remove a draft

## Trigger

A draft is no longer wanted.

## Outcome

The draft and its images are gone.

## Edge cases

- Undo within the six seconds keeps the draft.
