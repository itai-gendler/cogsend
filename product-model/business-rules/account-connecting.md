---
appliesTo:
  - { type: entity, id: account, effect: creates }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireSession }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
  - { kind: code, role: implementation, target: src/routes/api/connections/zernio/import/+server.ts }
---

# Only the signed-in Admin connects accounts

Connecting an account, directly, through Zernio or by import, happens only in the Admin's signed-in browser. An API key, however scoped, never connects one.

## Rationale

A key that already acts as the Admin must not be able to point the instance at accounts or apps somebody else controls.
