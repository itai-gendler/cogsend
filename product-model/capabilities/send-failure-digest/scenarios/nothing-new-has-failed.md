---
kind: edge
routes:
  web: Web
steps:
  - text: A tick finishes and nothing has failed since the last digest
    kind: condition
    unattended: true
    entities:
      - { entity: delivery, effect: reads, facts: [] }
      - { entity: instance, effect: reads, facts: [Last failure digest] }
    contexts: { web: { place: web::app::dashboard } }
  - text: The Product sends no email
    kind: condition
    entities:
      - { entity: instance, effect: reads, facts: [Failure email] }
    contexts: { web: { place: web::app::dashboard } }
---

# Nothing new has failed

## Trigger

A quiet day.

## Outcome

No email is sent.
