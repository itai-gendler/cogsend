---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Revoke on the tick token and confirms
    kind: actor
    actor: admin
    entities:
      - { entity: tick-token, effect: reads, facts: [Prefix] }
    contexts: { web: { place: web::app::settings } }
  - text: The Product removes the tick token
    kind: product
    actor: admin
    entities:
      - { entity: tick-token, effect: removes }
    contexts: { web: { place: web::app::settings } }
---

# Revoke the token

## Trigger

The external cron is no longer used.

## Outcome

No external caller can reach the tick with that token.
