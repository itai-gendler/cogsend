---
type: api
actors: [api-client]
entryPoints:
  - api: /api
references:
  - { kind: doc, role: intent, target: docs/api.md, title: API }
  - { kind: code, role: implementation, target: src/routes/api/+page.svelte }
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireScope }
---

# API

The HTTP API scripts call with the Admin's personal API key as a bearer token
or an X-API-Key header, without signing in.
