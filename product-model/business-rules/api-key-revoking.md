---
appliesTo:
  - { type: entity, id: api-key, effect: changes, to: Revoked }
permits:
  - actors: [admin]
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireSession }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
  - { kind: code, role: implementation, target: src/routes/api/key/+server.ts }
---

# Only the signed-in Admin revokes the API key

The personal API key is revoked only from Settings in a signed-in browser, so a leaked key cannot lock its owner out.
