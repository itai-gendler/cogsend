---
kind: primary
routes:
  api: API
steps:
  - text: "The API client asks to delete a platform's override of a post"
    kind: actor
    actor: api-client
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product removes the platform override
    kind: product
    actor: api-client
    entities:
      - { entity: platform-override, effect: removes }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Delete an override through the API

## Trigger

A script resets a platform to the Global text.

## Outcome

That platform gets the Global text.
