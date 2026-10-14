---
appliesTo:
  - { type: capability, id: generate-api-key }
  - { type: capability, id: generate-tick-token }
references:
  - { kind: code, role: implementation, target: src/lib/server/api-keys.ts#hashApiKey }
  - { kind: code, role: implementation, target: src/lib/server/tick-token.ts#hashTickToken }
---

# A new API key or tick token is shown once

The full key or token is shown only when it is generated; afterwards only its prefix is shown and only its hash is kept.
