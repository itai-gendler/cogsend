---
appliesTo:
  - { type: capability, id: enter-authenticator-code }
  - { type: capability, id: replace-authenticator }
  - { type: entity, id: admin, facts: [Backup codes] }
references:
  - { kind: code, role: implementation, target: src/lib/server/totp.ts#checkUserCode }
  - { kind: code, role: implementation, target: src/lib/domain/backup-codes.ts }
---

# A backup code works once

Each of the ten backup codes signs in, or proves the current second factor, only once; replacing the authenticator issues ten new ones and the old ones stop working.
