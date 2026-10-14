---
appliesTo:
  - { type: entity, id: admin, effect: changes, facts: [Email, Password] }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/routes/api/account/+server.ts }
---

# Only the signed-in Admin, with their current password, changes the login

The email and password are changed only from Settings in a signed-in browser, and only after the current password is entered again.
