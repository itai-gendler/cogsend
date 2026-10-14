---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin presses Clear all in the account list
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: "The Product empties the post's selected accounts"
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: changes, facts: [Selected accounts] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Clear all accounts

## Trigger

The Admin wants to pick the accounts again from nothing.

## Outcome

No account is selected for the post.
