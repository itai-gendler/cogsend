---
kind: primary
routes:
  web: Web
steps:
  - text: "The Admin changes the text in a platform's override tab"
    kind: actor
    actor: admin
    entities:
      - { entity: platform-override, effect: reads, facts: [Platform, Text] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product saves the platform override
    kind: product
    actor: admin
    entities:
      - { entity: platform-override, effect: changes, facts: [Text] }
      - { entity: post, effect: changes, facts: [Last edited] }
    contexts: { web: { place: web::app::composer } }
---

# Edit a platform tab

## Trigger

The tailored version needs another pass.

## Outcome

That platform gets the new text.
