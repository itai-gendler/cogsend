---
availability:
  - { place: web::app }
domain: accounts
references:
  - { kind: code, role: implementation, target: "src/routes/api/settings/platform-apps/[platform]/+server.ts" }
  - { kind: code, role: implementation, target: src/lib/server/platform-credentials.ts#deletePlatformCredentials }
---

# Remove a platform app

Remove the app details saved in the accounts dialog for LinkedIn, Threads or X; the platform needs setup again before new direct connections.
