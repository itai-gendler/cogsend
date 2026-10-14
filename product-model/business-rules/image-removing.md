---
appliesTo:
  - { type: entity, id: image, effect: removes }
permits:
  - actors: [admin]
  - actors: [api-client]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireScope }
  - { kind: code, role: implementation, target: src/lib/domain/api-scopes.ts#hasApiScope }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
---

# The Admin, or a Read + write key through the API, removes images

Images are removed in the composer or through the API with a Read + write key.
