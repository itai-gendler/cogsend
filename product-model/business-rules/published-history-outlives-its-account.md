---
appliesTo:
  - { type: capability, id: disconnect-account }
  - { type: capability, id: connect-account }
  - { type: capability, id: view-insights }
  - { type: entity, id: account }
references:
  - { kind: code, role: implementation, target: "src/routes/api/connections/[id]/+server.ts" }
  - { kind: code, role: implementation, target: src/lib/server/oauth-callback.ts#findExistingConnection }
---

# What an account published outlives the account

Disconnecting an account removes its unpublished deliveries but keeps those that went out, and archives the account so Posts and Insights still show them; reconnecting the same account brings it back with that history.
