---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Retry on a failed card
    kind: actor
    actor: admin
    entities:
      - { entity: delivery, effect: reads, facts: [Error] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product clears the error and attempts and sends the post again to each account that failed
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: changes, from: Failed, to: Queued, facts: [Error, Attempts] }
      - { entity: account, effect: reads, facts: [Credentials] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
  - text: The platform accepts it this time
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: changes, from: Queued, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Partly published, to: Published, facts: [] }
    contexts: { web: { place: web::app::posts } }
---

# Retry the failed accounts of a post

## Trigger

The cause of a failure has been fixed, or was temporary.

## Outcome

The post is published on the accounts that had failed.

## Edge cases

- A card with several failed accounts offers Retry N failed.
- Accounts that already published are not sent the post again.
