---
appliesTo:
  - { type: capability, id: generate-api-key }
  - { type: entity, id: api-key }
references:
  - { kind: code, role: implementation, target: src/lib/server/api-keys.ts#rotateApiKey }
---

# There is one active API key at a time

Generating a key revokes the active one, so at most one key is accepted.
