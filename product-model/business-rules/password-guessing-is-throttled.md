---
appliesTo:
  - { type: capability, id: sign-in }
  - { type: capability, id: change-login-settings }
references:
  - { kind: code, role: implementation, target: src/lib/server/auth-gate.ts#recordPasswordFailure }
---

# Eight wrong passwords from one address pause sign-in for fifteen minutes

Wrong passwords count per client address and, with a higher cap of forty, across all addresses; the same count covers the current-password check in Settings. A wrong email counts only against its address.

## Rationale

Counting per address keeps someone who knows the email from locking the owner out.
