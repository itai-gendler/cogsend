---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Duplicate on a draft card
    kind: actor
    actor: admin
    entities:
      - { entity: post, as: original, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product creates a Draft copy with the same text, accounts and overrides and copies of its images, and opens it in the composer
    kind: product
    actor: admin
    entities:
      - { entity: post, as: copy, effect: creates, to: Draft, facts: [Title, Text, Selected accounts, Last edited] }
      - { entity: platform-override, effect: creates, facts: [Platform, Text, Visibility, Content warning], with: copy }
      - { entity: image, effect: creates, facts: [Card, Order, Alt text, Format, Size, Dimensions], with: copy }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Duplicate a draft

## Trigger

The Admin wants a variation of something they wrote.

## Outcome

A new draft copy is open in the composer and the original is untouched.

## Edge cases

- An image whose file is missing is left out of the copy rather than failing it.
