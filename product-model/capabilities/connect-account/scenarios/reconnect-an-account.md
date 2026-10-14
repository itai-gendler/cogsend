---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin presses Reconnect on an account that needs reconnecting and goes through its flow again
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform, Handle] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Product finds the same account, stores its new credentials and keeps its history
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: changes, from: Needs reconnect, to: Active, facts: [Credentials, Display name, Avatar] }
    contexts: { web: { place: web::app::accounts } }
---

# Reconnect an account

## Trigger

A token stopped working, often a LinkedIn token after 60 days.

## Outcome

The account works again with its history intact.

## Edge cases

- Connecting an account that was disconnected while it had history revives it with that history.
