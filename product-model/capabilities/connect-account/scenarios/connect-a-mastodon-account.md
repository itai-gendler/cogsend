---
kind: primary
routes:
  web: Web
steps:
  - text: "The Admin chooses Connect new, then Mastodon, and enters their server's address"
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product registers itself on that server and sends the Admin there to approve CogSend
    kind: product
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Admin approves CogSend on their Mastodon server
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product connects the account and returns the Admin to Accounts with it listed
    kind: product
    actor: admin
    entities:
      - { entity: account, effect: creates, to: Active, facts: [Platform, Handle, Display name, Avatar, Server, Connected through, Credentials, Character limit] }
    contexts: { web: { place: web::app::accounts } }
---

# Connect a Mastodon account

## Trigger

The Admin wants their posts to reach Mastodon.

## Outcome

The Mastodon account is connected and can be ticked in the composer.

## Edge cases

- A server address that is not a public host is refused.
