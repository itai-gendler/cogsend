---
kind: primary
routes:
  web: Web
steps:
  - text: "The Admin types a description in an image's alt-text field"
    kind: actor
    actor: admin
    entities:
      - { entity: image, effect: reads, facts: [Alt text] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product saves it on the image
    kind: product
    actor: admin
    entities:
      - { entity: image, effect: changes, facts: [Alt text] }
    contexts: { web: { place: web::app::composer } }
---

# Describe an image

## Trigger

An image needs a description for people who cannot see it.

## Outcome

The image carries its alt text.
