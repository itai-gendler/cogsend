---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin chooses Connect through Zernio, pastes a Zernio key or keeps the stored one, picks a platform and a Zernio profile and presses Connect
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product sends the Admin through Zernio to the platform to approve
    kind: product
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Admin approves it
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product connects the account as one connected through Zernio and returns the Admin to Accounts
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: creates, to: Active, facts: [Platform, Handle, Display name, Avatar, Connected through, Credentials, Zernio API key] }
    contexts: { web: { place: web::app::accounts } }
---

# Connect through Zernio

## Trigger

The Admin would rather not register their own developer app.

## Outcome

The account is connected and publishes through Zernio.

## Edge cases

- Bluesky and Mastodon cannot be connected through Zernio from here.
