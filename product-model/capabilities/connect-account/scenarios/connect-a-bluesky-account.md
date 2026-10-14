---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin chooses Bluesky and enters their handle and an app password
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product signs in to Bluesky with them and connects the account
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: creates, to: Active, facts: [Platform, Handle, Display name, Avatar, Server, Connected through, Credentials] }
    contexts: { web: { place: web::app::accounts } }
---

# Connect a Bluesky account

## Trigger

The Admin wants their posts to reach Bluesky.

## Outcome

The Bluesky account is connected.

## Edge cases

- Bluesky refusing the handle or app password connects nothing and says why.
- The Admin's main Bluesky password is never the one to use.
