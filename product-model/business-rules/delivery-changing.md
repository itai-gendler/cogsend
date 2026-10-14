---
appliesTo:
  - { type: entity, id: delivery, effect: changes }
permits:
  - actors: [admin]
  - actors: [api-client]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
  - related: [{ verb: has, entity: post }, { verb: owns, entity: admin }, { verb: connects, entity: ai-agent }]
    when:
      - { entity: api-key, fact: Scope, is: Read + write }
  - unattended: true
  - actors: [external-cron]
references:
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireScope }
  - { kind: code, role: implementation, target: src/lib/domain/api-scopes.ts#hasApiScope }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
  - { kind: code, role: implementation, target: src/routes/api/targets/bulk/+server.ts }
---

# The Admin, a Read + write key or a tick moves deliveries

Cancelling, rescheduling and retrying deliveries needs the Admin or a Read + write API key. Ticks, from the Worker's own cron, an external cron or Tick now, send what is due.
