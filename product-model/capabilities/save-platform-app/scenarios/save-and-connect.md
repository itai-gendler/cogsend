---
kind: primary
routes:
  web: Web
steps:
  - text: "On a platform that needs setup, the Admin registers the shown redirect address with the platform, enters the app's client id and secret and presses Save and connect"
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::accounts } }
  - text: The Product stores the platform app and starts connecting an account on that platform
    kind: product
    actor: admin
    entities:
      - { entity: platform-app, effect: creates, facts: [Platform, Client ID, Client secret, Source] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::accounts } }
---

# Save and connect

## Trigger

The Admin created a developer app on LinkedIn, Threads or X.

## Outcome

The platform is set up and the Admin is approving the first account.
