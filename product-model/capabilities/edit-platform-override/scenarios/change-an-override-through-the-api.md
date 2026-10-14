---
kind: primary
routes:
  api: API
steps:
  - text: The API client sends new text for a platform the post already overrides
    kind: actor
    actor: api-client
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product saves the platform override
    kind: product
    actor: api-client
    entities:
      - { entity: platform-override, effect: changes, facts: [Text] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Change an override through the API

## Trigger

A script updates the tailored version.

## Outcome

That platform gets the new text.
