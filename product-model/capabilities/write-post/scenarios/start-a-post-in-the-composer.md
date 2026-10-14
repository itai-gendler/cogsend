---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin opens Compose and types the first words of a post
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: "The Product saves a new Draft post with that text and the Admin's preselected accounts ticked"
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: creates, to: Draft, facts: [Text, Selected accounts, Last edited] }
      - { entity: admin, effect: reads, facts: [Preselected accounts, Default Mastodon visibility] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The composer says Saved and the post is listed under Posts, Drafts
    kind: condition
    entities:
      - { entity: post, effect: reads, facts: [Last edited] }
    contexts: { web: { place: web::app::composer } }
---

# Start a post in the composer

## Trigger

The Admin has something to post.

## Outcome

A Draft post exists and keeps saving itself as the Admin types.

## Edge cases

- With no preselected accounts, every active account starts ticked.
- Write on a composer that holds a post saves that post and opens a blank one; a scheduled post keeps its time. On an empty composer Write is hidden.
- Switching to another tab or app saves at once.
