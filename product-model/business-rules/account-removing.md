---
appliesTo:
  - { type: entity, id: account, effect: removes }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireSession }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
---

# Only the signed-in Admin removes accounts

An account without published history is removed only when the signed-in Admin disconnects it.
