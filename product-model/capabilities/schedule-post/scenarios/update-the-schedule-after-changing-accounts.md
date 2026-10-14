---
kind: alternative
routes:
  web: Web
steps:
  - text: On a scheduled post the Admin has ticked a new account and unticked another, and the post says which accounts differ
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Selected accounts] }
      - { entity: account, effect: reads, facts: [Handle] }
    contexts: { web: { place: web::app::composer } }
  - text: The Admin presses Update schedule
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: "The Product schedules the newly ticked account at the post's time and cancels the unticked one"
    kind: product
    actor: admin
    entities:
      - { entity: delivery, as: added, effect: creates, to: Scheduled, facts: [Scheduled time, Attempts] }
      - { entity: delivery, as: dropped, effect: changes, from: Scheduled, to: Cancelled, facts: [] }
      - { entity: post, effect: reads, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Update the schedule after changing accounts

## Trigger

The Admin changed where a scheduled post goes.

## Outcome

The schedule matches exactly the ticked accounts.
