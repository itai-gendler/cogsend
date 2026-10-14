---
appliesTo:
  - { type: entity, id: image, effect: changes }
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

# The Admin, or a Read + write key through the API, changes an image's alt text

Alt text is changed in the composer or through the API with a Read + write key.
