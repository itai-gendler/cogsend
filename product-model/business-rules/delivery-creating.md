---
appliesTo:
  - { type: entity, id: delivery, effect: creates }
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
  - { kind: code, role: implementation, target: src/routes/api/mcp/+server.ts }
---

# The Admin, or a Read + write key, publishes and schedules posts

Publishing a post or scheduling it, which creates its deliveries, needs the Admin or a Read + write API key. A Read-only key never publishes.
