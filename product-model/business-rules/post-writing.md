---
appliesTo:
  - { type: entity, id: post, effect: creates }
permits:
  - actors: [admin]
  - actors: [api-client]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
  - related: [{ verb: owns, entity: admin }, { verb: connects, entity: ai-agent }]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireScope }
  - { kind: code, role: implementation, target: src/lib/domain/api-scopes.ts#hasApiScope }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
---

# The Admin, or a Read + write key, writes posts

The Admin writes posts in the app. A script or an AI agent writes them only with a Read + write API key; a Read-only key can list and read posts but not create them.
