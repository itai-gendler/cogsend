---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Edit Post on a scheduled card
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
  - text: The Product opens it in the composer and shows above the text when and to which accounts it goes out
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text, Selected accounts] }
      - { entity: delivery, effect: reads, facts: [Scheduled time, Error] }
      - { entity: account, effect: reads, facts: [Handle] }
    contexts: { web: { place: web::app::composer } }
---

# Open a scheduled post

## Trigger

The Admin wants to check or change a scheduled post.

## Outcome

The post is open; edits save as the Admin types and what is saved when the time comes is what goes out.

## Edge cases

- A few minutes before the time the post says so; while it is being sent, editing pauses until the result is in.
- A post that went out on some accounts, failed on others or is retrying shows each account's result.
