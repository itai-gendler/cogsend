---
kind: edge
routes:
  web: Web
steps:
  - text: The Admin submits the form after the Admin was already created
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product finds the Admin already exists, creates nothing and says so
    kind: condition
    entities:
      - { entity: admin, effect: reads, facts: [] }
    contexts: { web: { place: web::login::sign-in } }
---

# Create an account that already exists

## Trigger

Two browsers race to create the account, or a stale page is submitted.

## Outcome

The instance keeps exactly its first account.
