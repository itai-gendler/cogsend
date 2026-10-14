---
availability:
  - { place: web::app }
domain: settings
references:
  - { kind: code, role: implementation, target: src/routes/api/key/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/api-keys.ts#revokeApiKeys }
---

# Revoke the API key

Stop the Admin's personal API key, so scripts and agents using it are refused.
