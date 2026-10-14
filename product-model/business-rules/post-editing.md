---
appliesTo:
  - { type: entity, id: post, effect: changes }
permits:
  - actors: [admin]
  - actors: [api-client]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
  - related: [{ verb: owns, entity: admin }, { verb: connects, entity: ai-agent }]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
  - unattended: true
  - actors: [external-cron]
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireScope }
  - { kind: code, role: implementation, target: src/lib/domain/api-scopes.ts#hasApiScope }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
---

# The Admin, a Read + write key or the scheduler changes posts

The Admin edits posts in the app, and scripts and agents with a Read + write key change them through the API. The Product moves a post between its states as its deliveries go out on a tick, whether the Worker's own cron or an external cron calls it.
