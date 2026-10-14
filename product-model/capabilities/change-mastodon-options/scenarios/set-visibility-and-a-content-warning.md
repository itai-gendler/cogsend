---
kind: primary
routes:
  web: Web
steps:
  - text: With a Mastodon account ticked, the Admin opens Mastodon Options and picks a visibility and a content warning
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::composer } }
  - text: "The Product keeps them in the post's Mastodon platform override"
    kind: product
    actor: admin
    entities:
      - { entity: platform-override, effect: creates, facts: [Platform, Visibility, Content warning] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Set visibility and a content warning

## Trigger

A post should go out Unlisted or behind a content warning on Mastodon.

## Outcome

The post goes out on Mastodon with that visibility and warning.

## Edge cases

- Visibility is Public, Unlisted, Followers or Direct.
- Changing the options again changes the same override.
