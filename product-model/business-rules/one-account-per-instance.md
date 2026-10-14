---
appliesTo:
  - { type: capability, id: create-admin-account }
  - { type: entity, id: admin }
  - { type: entity, id: instance, facts: [Encryption key] }
references:
  - { kind: code, role: implementation, target: src/routes/api/auth/claim/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/auth.ts#needsSetup }
  - { kind: doc, role: intent, target: docs/configuration.md, title: "The login" }
---

# An instance has exactly one account, created by whoever holds its encryption key

The login page creates the account only while none exists and only for someone who enters the encryption key the instance was deployed with; once it exists, the form is gone. Otherwise the operator creates it from a terminal before the first request.

## Rationale

A fresh instance must not belong to whoever finds its address first.
