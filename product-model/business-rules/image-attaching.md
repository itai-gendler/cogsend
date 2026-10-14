---
appliesTo:
  - { type: entity, id: image, effect: creates }
permits:
  - actors: [admin]
  - actors: [api-client]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireScope }
  - { kind: code, role: implementation, target: src/lib/domain/api-scopes.ts#hasApiScope }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/media/+server.ts" }
---

# The Admin, or a Read + write key through the API, attaches images

Images are attached in the composer or through the API with a Read + write key. The MCP server does not handle media.
