---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses Generate tick token and confirms
    kind: actor
    actor: admin
    entities:
      - { entity: tick-token, effect: reads, facts: [] }
    contexts: { web: { place: web::app::settings } }
  - text: The Product creates the tick token and shows it once with the tick address to call
    kind: product
    actor: admin
    entities:
      - { entity: tick-token, effect: creates, facts: [Prefix, Created] }
    contexts: { web: { place: web::app::settings } }
  - text: The Admin copies it into their cron service and presses I have saved it
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
---

# Generate a token for an external cron

## Trigger

The Cloudflare account has no cron trigger left, or the Admin wants a backup tick.

## Outcome

An external cron can publish scheduled posts.
