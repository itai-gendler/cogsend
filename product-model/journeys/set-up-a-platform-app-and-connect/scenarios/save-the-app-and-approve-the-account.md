---
kind: primary
result: achieved
routes:
  web: Web
steps:
  - text: "On a platform that needs setup, the Admin enters the app's client id and secret and presses Save and connect"
    kind: actor
    capability: save-platform-app
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product stores the platform app and sends the Admin to the platform to approve it
    kind: product
    capability: save-platform-app
    actor: admin
    entities:
      - { entity: platform-app, effect: creates, facts: [Platform, Client ID, Client secret, Source] }
    contexts: { web: { place: web::app::accounts } }
  - text: The Admin approves the app on the platform
    kind: actor
    capability: connect-account
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product connects the account and returns the Admin to Accounts
    kind: product
    capability: connect-account
    actor: admin
    entities:
      - { entity: account, effect: creates, to: Active, facts: [Platform, Handle, Display name, Avatar, Connected through, Credentials] }
    contexts: { web: { place: web::app::accounts } }
---

# Save the app and approve the account

## Trigger

The Admin created a developer app and wants to post there.

## Outcome

The account is connected through the Admin's own app.
