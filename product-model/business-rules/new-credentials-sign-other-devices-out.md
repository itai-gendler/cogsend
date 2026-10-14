---
appliesTo:
  - { type: capability, id: change-login-settings }
  - { type: capability, id: replace-authenticator }
references:
  - { kind: code, role: implementation, target: src/lib/server/auth.ts#revokeOtherSessions }
  - { kind: code, role: implementation, target: src/routes/api/account/+server.ts }
---

# A new password or authenticator signs other devices out

Saving a new password ends every session, the current one included; enrolling a replacement authenticator ends every other session.
