---
kind: primary
routes:
  web: Web
steps:
  - text: With an X account ticked, the Admin pastes a link to an X post at the end of a card
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: "The Product keeps the link at the end of the card's text and shows it as a quote card with the quoted author and text"
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: changes, facts: [Text, Last edited] }
    contexts: { web: { place: web::app::composer } }
---

# Paste a link to an X post

## Trigger

The Admin wants to comment on someone's X post.

## Outcome

The card quotes that post on X, and the other ticked platforms get the same text with the link.

## Edge cases

- A link to an X post anywhere but the very end stays a plain link, and the card offers to quote it instead.
- A card quotes one post; another X link pasted into it stays a plain link.
- On Bluesky and LinkedIn a link to an X post gets a card with its author and text.
