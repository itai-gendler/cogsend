---
kind: primary
routes:
  api: API
steps:
  - text: The API client asks for one post
    kind: actor
    actor: api-client
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product answers with its text, overrides, images and deliveries
    kind: product
    actor: api-client
    entities:
      - { entity: post, effect: reads, facts: [Title, Text, Selected accounts] }
      - { entity: platform-override, effect: reads, facts: [Platform, Text] }
      - { entity: image, effect: reads, facts: [Card, Alt text] }
      - { entity: delivery, effect: reads, facts: [Scheduled time, Error, Link] }
    contexts: { api: { place: api } }
---

# Fetch a draft through the API

## Trigger

A script needs a post's details.

## Outcome

The script has the whole post.
