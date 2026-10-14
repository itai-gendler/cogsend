---
kind: primary
routes:
  api: API
steps:
  - text: The API client sends a text and optionally a platform
    kind: actor
    actor: api-client
    entities: []
    contexts: { api: { place: api } }
  - text: The Product answers with its length per platform and the issues each platform would raise
    kind: product
    actor: api-client
    entities: []
    contexts: { api: { place: api } }
---

# Validate text through the API

## Trigger

A script wants to know whether a text fits before posting it.

## Outcome

The script knows which platforms would refuse the text and why.

## Edge cases

- Text over 200,000 characters is refused.
