---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin presses the re-sync button on an unlinked platform tab
    kind: actor
    actor: admin
    entities:
      - { entity: platform-override, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product removes the platform override and the tab shows the Global text again
    kind: product
    actor: admin
    entities:
      - { entity: platform-override, effect: removes }
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::composer } }
---

# Re-sync a tab to Global

## Trigger

The tailored version is no longer wanted.

## Outcome

That platform gets the Global text.

## Edge cases

- A Mastodon tab that still carries a visibility or content warning keeps those options.
