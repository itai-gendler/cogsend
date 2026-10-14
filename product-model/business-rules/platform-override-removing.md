---
appliesTo:
  - { type: entity, id: platform-override, effect: removes }
permits:
  - actors: [admin]
  - actors: [api-client]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
  - related: [{ verb: has, entity: post }, { verb: owns, entity: admin }, { verb: connects, entity: ai-agent }]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireScope }
  - { kind: code, role: implementation, target: src/lib/domain/api-scopes.ts#hasApiScope }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
---

# The Admin, or a Read + write key, removes platform overrides

A platform's own version of a post is removed in the composer, or by a script or agent with a Read + write API key.
