---
appliesTo:
  - { type: entity, id: account, effect: changes, to: Archived }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireSession }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
  - { kind: code, role: implementation, target: "src/routes/api/connections/[id]/+server.ts" }
---

# Only the signed-in Admin disconnects accounts

Disconnecting an account happens only in the Admin's signed-in browser; an API key never disconnects one.
