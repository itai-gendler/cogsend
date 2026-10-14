---
kind: primary
routes:
  web: Web
steps:
  - text: With more than one account ticked, the Admin chooses Add override… and a platform
    kind: actor
    actor: admin
    entities:
      - { entity: account, effect: reads, facts: [Platform] }
    contexts: { web: { place: web::app::composer } }
  - text: "The Admin rewrites the text in that platform's tab"
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::composer } }
  - text: The Product keeps a platform override with that text for the post, leaving Global untouched
    kind: product
    actor: admin
    entities:
      - { entity: platform-override, effect: creates, facts: [Platform, Text] }
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { web: { place: web::app::composer } }
---

# Add an override tab

## Trigger

One platform needs different words, shorter for X or longer for LinkedIn.

## Outcome

That platform gets its own text and every other account keeps the Global text.

## Edge cases

- The tab is unlinked from Global from then on: later Global edits do not reach it.
