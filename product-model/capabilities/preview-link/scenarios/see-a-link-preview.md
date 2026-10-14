---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin writes a URL in a card
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: "The Product fetches the page's title, description and picture and shows the preview card"
    kind: product
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::composer } }
---

# See a link preview

## Trigger

A post links to an article.

## Outcome

The Admin sees how the link will look.
