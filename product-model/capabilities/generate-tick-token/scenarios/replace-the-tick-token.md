---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin presses Generate replacement on the tick token and confirms
    kind: actor
    actor: admin
    entities:
      - { entity: tick-token, as: old, effect: reads, facts: [Prefix] }
    contexts: { web: { place: web::app::settings } }
  - text: The Product removes the old token and creates a new one, shown once
    kind: product
    actor: admin
    entities:
      - { entity: tick-token, as: old, effect: removes }
      - { entity: tick-token, as: new, effect: creates, facts: [Prefix, Created] }
    contexts: { web: { place: web::app::settings } }
---

# Replace the tick token

## Trigger

The token may have leaked.

## Outcome

Only the new token reaches the tick.
