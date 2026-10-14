---
kind: validation
routes:
  web: Web
steps:
  - text: The Admin enters an email and password that do not match the Admin's
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product refuses with Invalid credentials and counts the failure against this address
    kind: condition
    entities:
      - { entity: admin, effect: reads, facts: [Email, Password] }
    contexts: { web: { place: web::login::sign-in } }
---

# Sign in with a wrong password

## Trigger

The Admin mistypes their password, or someone guesses.

## Outcome

Nobody is signed in, and the answer does not say whether the email was right.

## Edge cases

- After eight failures from one address, or forty across all addresses, sign-in is refused for fifteen minutes with Too many attempts.
