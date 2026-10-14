---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks for insights over a number of days
    kind: actor
    actor: api-client
    entities: []
    contexts: { api: { place: api } }
  - text: The Product answers with the same counts, series and failure reasons
    kind: product
    actor: api-client
    entities:
      - { entity: delivery, effect: reads, facts: [Error] }
      - { entity: account, effect: reads, facts: [Platform, Handle] }
    contexts: { api: { place: api } }
---

# Read insights through the API

## Trigger

A script reports on posting.

## Outcome

The script has the numbers.
