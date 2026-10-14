---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin unticks an account in the account list
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform, Handle] }
    contexts: { web: { place: web::app::composer } }
  - text: "The Product removes it from the post's selected accounts"
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: changes, facts: [Selected accounts] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Untick an account

## Trigger

The post should not go to that account.

## Outcome

The account is no longer selected for the post.

## Edge cases

- On a scheduled post unticking does not unschedule it until Update schedule, Publish now or Unschedule.
