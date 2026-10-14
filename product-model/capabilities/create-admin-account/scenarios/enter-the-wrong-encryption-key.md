---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin enters an encryption key, an email and a password on a fresh deployment
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The key is not the one the Instance was deployed with, so the Product creates nothing and says so
    kind: condition
    entities:
      - { entity: instance, effect: reads, facts: [Encryption key] }
    contexts: { web: { place: web::login::sign-in } }
---

# Enter the wrong encryption key

## Trigger

Someone who found a fresh instance's address tries to create its account.

## Outcome

No account is created; only whoever holds the deployment's key can create it.
