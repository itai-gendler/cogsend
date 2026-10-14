---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin opens the login page of a fresh deployment where no Admin exists yet
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The Admin enters the deployment's encryption key, an email and a password
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product checks the key against the Instance's encryption key
    kind: condition
    entities:
      - { entity: instance, effect: reads, facts: [Encryption key] }
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product creates the Admin with that email and password and sends them to set up an authenticator
    kind: product
    actor: admin
    entities:
      - { entity: admin, effect: creates, to: Awaiting two-factor setup, facts: [Email, Password, Time zone] }
    contexts: { web: { place: web::login::set-up-authenticator } }
---

# Create the account with the encryption key

## Trigger

Someone who deployed a new instance opens it for the first time.

## Outcome

The instance has its one account, and its Admin is setting up an
authenticator.

## Edge cases

- An email that is not an email address, or a password under eight characters, is refused before anything is created.
