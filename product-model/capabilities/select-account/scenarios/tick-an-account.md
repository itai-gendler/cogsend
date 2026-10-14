---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin opens the account list and ticks an account
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform, Handle] }
    contexts: { web: { place: web::app::composer } }
  - text: "The Product adds it to the post's selected accounts and its counters follow the strictest limit"
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: changes, facts: [Selected accounts] }
      - { entity: account, effect: reads, facts: [Character limit] }
    contexts: { web: { place: web::app::composer } }
---

# Tick an account

## Trigger

The Admin wants a post to go to another account.

## Outcome

The account is among the post's selected accounts.

## Edge cases

- An account that needs reconnecting is marked in the list.
- On a scheduled post ticking an account does not schedule it; the post says which accounts differ until Update schedule applies them.
