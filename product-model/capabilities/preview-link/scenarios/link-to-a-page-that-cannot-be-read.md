---
kind: edge
routes:
  web: Web
steps:
  - text: The Admin writes a URL whose page does not answer or is not a public web page
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: The Product shows no preview card and the post stays as written
    kind: condition
    entities:
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::composer } }
---

# Link to a page that cannot be read

## Trigger

The linked page is down, private or too large.

## Outcome

No preview is shown; publishing is not affected.
