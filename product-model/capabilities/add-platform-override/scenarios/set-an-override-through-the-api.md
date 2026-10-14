---
kind: primary
routes:
  api: API
steps:
  - text: The API client sends text for a platform the post has no override for
    kind: actor
    actor: api-client
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
  - text: The Product creates the platform override for the post
    kind: product
    actor: api-client
    entities:
      - { entity: platform-override, effect: creates, facts: [Platform, Text] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { api: { place: api } }
---

# Set an override through the API

## Trigger

A script tailors a post for one platform.

## Outcome

The post has an override for that platform.

## Edge cases

- A platform other than Mastodon, Bluesky, LinkedIn, Threads or X is refused.
- At most 100 explicit thread cards are accepted.
