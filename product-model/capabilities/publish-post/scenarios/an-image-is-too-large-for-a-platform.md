---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin presses Publish on a post
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [] }
      - { entity: account, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::composer } }
  - text: "An image is over a ticked platform's limit, so the Product stops before sending and says which platform to untick"
    kind: condition
    entities:
      - { entity: image, effect: reads, facts: [Size] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# An image is too large for a platform

## Trigger

A post carries an image Bluesky or X would refuse.

## Outcome

Nothing is sent until the image or the account choice changes.
