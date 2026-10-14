---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin chooses to sign out from the profile menu
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app } }
  - text: The Product ends this browser's session
    kind: product
    actor: admin
    entities: []
    contexts: { web: { place: web::app } }
---

# Sign out of the app

## Trigger

The Admin is done on a shared or borrowed device.

## Outcome

This browser is signed out; other devices stay signed in.
