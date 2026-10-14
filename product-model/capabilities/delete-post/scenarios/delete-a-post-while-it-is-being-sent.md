---
kind: edge
routes:
  web: Web
steps:
  - text: The Admin tries to delete a post one of whose deliveries is being sent
    kind: actor
    actor: admin
    entities:
      - { entity: post, effect: reads, facts: [] }
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
  - text: The Product refuses with Publishing in progress, try again shortly
    kind: condition
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { web: { place: web::app::composer } }
---

# Delete a post while it is being sent

## Trigger

The Admin deletes a post in the seconds it is going out.

## Outcome

The post stays until its delivery settles, so the published post keeps its record.
