---
kind: primary
result: achieved
routes:
  web: Web
steps:
  - text: The Admin presses Post again on a published card
    kind: actor
    capability: duplicate-post
    actor: admin
    entities:
      - { entity: post, as: original, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product creates a Draft copy and opens it in the composer
    kind: product
    capability: duplicate-post
    actor: admin
    entities:
      - { entity: post, as: copy, effect: creates, to: Draft, facts: [Title, Text, Selected accounts, Last edited] }
    contexts: { web: { place: web::app::composer } }
  - text: "The Admin updates the copy's text"
    kind: actor
    capability: edit-post
    actor: admin
    entities:
      - { entity: post, as: copy, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product saves the copy
    kind: product
    capability: edit-post
    actor: admin
    entities:
      - { entity: post, as: copy, effect: changes, facts: [Text, Last edited] }
    contexts: { web: { place: web::app::composer } }
---

# Duplicate a published post and rework it

## Trigger

A post did well and the Admin wants to share it again.

## Outcome

A refreshed copy is saved in the composer; the original stays as it went out.
