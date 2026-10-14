---
kind: alternative
routes:
  web: Web
steps:
  - text: The Admin presses Quote on X on a post that published to X
    kind: actor
    actor: admin
    entities:
      - { entity: delivery, effect: reads, facts: [Link] }
      - { entity: post, as: original, effect: reads, facts: [] }
    contexts: { web: { place: web::app::posts } }
  - text: "The Product creates a new Draft post whose text is that X post's link, ticked for the X account that posted it, and opens it in the composer"
    kind: product
    actor: admin
    entities:
      - { entity: post, as: quote, effect: creates, to: Draft, facts: [Text, Selected accounts, Last edited] }
      - { entity: account, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::composer } }
---

# Quote a published post from Posts

## Trigger

The Admin wants to follow up on something that went out on X.

## Outcome

A new post quoting it is open in the composer.
