---
appliesTo:
  - { type: capability, id: generate-tick-token }
  - { type: capability, id: publish-due-posts }
references:
  - { kind: code, role: implementation, target: src/hooks.server.ts }
  - { kind: code, role: implementation, target: src/lib/server/require.ts#assertSchedulerOrTickToken }
---

# The tick token reaches the tick and nothing else

The tick token is accepted by the tick address only; it reads nothing and changes nothing else.
