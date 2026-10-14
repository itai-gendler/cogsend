---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin opens the calendar next to Publish and chooses when the post goes out
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Selected accounts] }
      - { entity: account, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product schedules a delivery for each ticked account at that time
    kind: product
    actor: admin
    entities:
      - { entity: delivery, effect: creates, to: Scheduled, facts: [Scheduled time, Attempts] }
      - { entity: post, effect: changes, from: Draft, to: Scheduled, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The composer empties for the next post and links to the scheduled one in Posts
    kind: condition
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Schedule from the composer

## Trigger

A post should go out later.

## Outcome

The post waits in Posts, Scheduled until a tick publishes it.

## Decision points

### When

How does the Admin set the time?

- Publish in an offset of minutes, hours or days → the time is that far from now, one hour by default
- A Specific Date and time → the time is that moment in the Admin's own time zone

## Edge cases

- Opening a scheduled post again starts the calendar on its current time, so confirming without a change keeps it.
- More than ten ticked accounts are refused with Too many connections (max 10).
