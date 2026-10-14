---
kind: validation
routes:
  tick: Scheduler tick
steps:
  - text: The External cron posts to the tick address with a revoked or wrong token
    kind: actor
    actor: external-cron
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { tick: { place: scheduler-tick } }
  - text: The Product refuses the call and publishes nothing
    kind: condition
    entities:
      - { entity: tick-token, effect: reads, facts: [] }
    contexts: { tick: { place: scheduler-tick } }
---

# Call the tick without a valid credential

## Trigger

The token was replaced in Settings but not in the cron service.

## Outcome

Nothing is published until the cron service has the current token.
