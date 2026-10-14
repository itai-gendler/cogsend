---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin chooses LinkedIn, Threads or X, whose platform app is set up
    kind: actor
    actor: admin
    entities:
      - { entity: platform-app, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Product sends the Admin to the platform to approve the app
    kind: product
    actor: admin
    entities:
      - { entity: platform-app, effect: reads, facts: [Client ID] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Admin approves it on the platform
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product connects the account and returns the Admin to Accounts with it listed
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: creates, to: Active, facts: [Platform, Handle, Display name, Avatar, Connected through, Credentials] }
    contexts: { web: { place: web::app::accounts } }
---

# Connect a LinkedIn, Threads or X account

## Trigger

The Admin wants their posts to reach a platform that needs a developer app.

## Outcome

The account is connected through the Admin's own app.

## Edge cases

- A LinkedIn account connected through the Admin's own app needs reconnecting every 60 days.
