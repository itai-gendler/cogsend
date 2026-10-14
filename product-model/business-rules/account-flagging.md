---
appliesTo:
  - { type: entity, id: account, effect: changes, to: Needs reconnect }
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
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#isAuthFailure }
  - { kind: code, role: implementation, target: "src/routes/api/connections/[id]/verify/+server.ts" }
---

# The Admin, a Read + write key or a tick marks an account as needing reconnection

An account is marked as needing reconnection when its platform refuses its credentials: on a check by the signed-in Admin, or while publishing for the Admin, a script or agent with a Read + write key, or a tick.
