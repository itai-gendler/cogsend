---
appliesTo:
  - { type: entity, id: api-key, effect: creates }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireSession }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
  - { kind: code, role: implementation, target: src/routes/api/key/+server.ts }
---

# Only the signed-in Admin generates the API key

The personal API key is generated only from Settings in a signed-in browser; a key never mints its own replacement.
