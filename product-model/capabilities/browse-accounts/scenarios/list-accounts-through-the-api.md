---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks for the connected accounts
    kind: actor
    actor: api-client
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: "The Product answers with each account's id, platform, handle and state"
    kind: product
    actor: api-client
    entities:
      - { entity: account, effect: reads, facts: [Platform, Handle, Display name] }
    contexts: { api: { place: api } }
---

# List accounts through the API

## Trigger

A script needs the ids to publish to.

## Outcome

The script knows the accounts.
