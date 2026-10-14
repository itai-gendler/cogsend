---
kind: primary
result: achieved
routes:
  web: Web
steps:
  - text: The Admin enters their current password and a new one and presses Save login
    kind: actor
    capability: change-login-settings
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
  - text: The Product saves the new password, signs every device out and sends the Admin to sign in
    kind: product
    capability: change-login-settings
    actor: admin
    entities:
      - { entity: admin, effect: changes, facts: [Password] }
    contexts: { web: { place: web::app::settings } }
  - text: The Admin signs in with the new password
    kind: actor
    capability: sign-in
    actor: admin
    entities: []
    contexts: { web: { place: web::login::sign-in } }
  - text: The Product accepts it and asks for an authenticator code
    kind: product
    capability: sign-in
    actor: admin
    entities:
      - { entity: admin, effect: reads, facts: [Email, Password] }
    contexts: { web: { place: web::login::enter-code } }
---

# Save a new password and sign in

## Trigger

The Admin changes their password.

## Outcome

The Admin is past the password step with the new password.
