---
appliesTo:
  - { type: entity, id: admin, effect: changes, facts: [Authenticator] }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/lib/server/totp.ts#rotateStart }
  - { kind: code, role: implementation, target: src/lib/server/totp.ts#enrollConfirm }
---

# Only the Admin, proving a current code, changes the second factor

An authenticator is enrolled while signing in, or replaced from Settings after entering a current authenticator or backup code.
