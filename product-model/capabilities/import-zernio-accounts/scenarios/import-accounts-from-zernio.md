---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin pastes a Zernio key and presses Show my Zernio accounts
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Product lists the Zernio accounts it can post to, marking those already imported
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Handle] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Admin ticks some and presses Import
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product connects each ticked account as one connected through Zernio, keeping the key for next time
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: creates, to: Active, facts: [Platform, Handle, Display name, Avatar, Connected through, Credentials, Zernio API key] }
    contexts: { web: { place: web::app::accounts } }
---

# Import accounts from Zernio

## Trigger

The Admin already uses Zernio.

## Outcome

The imported accounts are connected and behave like any other.

## Edge cases

- Next time the field can be left blank and the stored key is used; pasting a new one replaces it.
