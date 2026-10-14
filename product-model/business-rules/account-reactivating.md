---
appliesTo:
  - { type: entity, id: account, effect: changes, to: Active }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireSession }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
  - { kind: code, role: implementation, target: "src/routes/api/connections/[id]/verify/+server.ts" }
---

# Only the signed-in Admin reconnects or checks accounts

Reconnecting an account or checking it back to active happens only in the Admin's signed-in browser; an API key never re-verifies an account.
