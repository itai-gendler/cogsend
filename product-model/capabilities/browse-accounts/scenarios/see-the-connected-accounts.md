---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin opens Accounts
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Product lists each connected account with its platform, handle, name and picture, marking those connected through Zernio and those that need reconnecting
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform, Handle, Display name, Avatar, Connected through] }
    contexts: { web: { place: web::app::accounts } }
---

# See the connected accounts

## Trigger

The Admin checks which accounts CogSend can post to.

## Outcome

The Admin sees every connected account and which need attention.
