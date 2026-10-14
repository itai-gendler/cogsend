---
availability:
  - { place: web::app }
domain: settings
references:
  - { kind: code, role: implementation, target: src/routes/api/key/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/api-keys.ts#rotateApiKey }
  - { kind: code, role: implementation, target: src/routes/settings/+page.svelte }
  - { kind: doc, role: intent, target: docs/api.md, title: "API" }
---

# Generate an API key

Create the Admin's personal API key under Settings, API access, choosing Read-only or Read + write. The key is shown once; generating a replacement stops the old key at once.
