---
kind: primary
routes:
  tick: Scheduler tick
steps:
  - text: The External cron posts to the tick address with the tick token
    kind: actor
    actor: external-cron
    entities:
      - { entity: tick-token, effect: reads, facts: [] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { tick: { place: scheduler-tick } }
  - text: The Product records the tick and publishes the deliveries that are due
    kind: product
    actor: external-cron
    entities:
      - { entity: instance, effect: changes, facts: [Last tick] }
      - { entity: delivery, effect: changes, from: Scheduled, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Scheduled, to: Published, facts: [] }
    contexts: { tick: { place: scheduler-tick } }
---

# An external cron calls the tick

## Trigger

The instance's own cron trigger is not available, or an external cron is a backup.

## Outcome

Scheduled posts go out on the external cron's cadence.

## Edge cases

- Ticks are idempotent: a duplicated or late call publishes nothing twice.
