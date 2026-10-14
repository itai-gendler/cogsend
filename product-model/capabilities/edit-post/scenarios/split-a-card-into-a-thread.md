---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin types --- in a card, presses + Thread, or pastes a long draft
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: The Product splits the text into cards that each fit the strictest limit of the ticked accounts
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: changes, facts: [Text, Last edited] }
      - { entity: account, effect: reads, facts: [Platform, Character limit] }
    contexts: { web: { place: web::app::composer } }
---

# Split a card into a thread

## Trigger

The post is too long for one card.

## Outcome

The post is a thread of cards, each within every ticked platform's limit.

## Edge cases

- Pasted text with --- on lines of their own splits on those instead.
- Alt with an arrow key moves the current card up or down the thread.
- A card's × removes it.
