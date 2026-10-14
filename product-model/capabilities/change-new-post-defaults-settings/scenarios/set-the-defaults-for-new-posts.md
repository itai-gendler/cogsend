---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin picks a default Mastodon visibility and switches on the accounts every new draft should start with
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform, Display name] }
    contexts: { web: { place: web::app::settings } }
  - text: "The Product saves them as the Admin's new post defaults"
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: changes, facts: [Default Mastodon visibility, Preselected accounts] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::settings } }
---

# Set the defaults for new posts

## Trigger

The Admin usually posts to the same few accounts.

## Outcome

New posts start with those accounts ticked and that visibility.

## Edge cases

- With no account switched on, new posts start with every active account ticked.
