---
availability:
  - { place: web::app }
domain: accounts
references:
  - { kind: code, role: implementation, target: "src/routes/api/settings/platform-apps/[platform]/+server.ts" }
  - { kind: code, role: implementation, target: src/lib/server/platform-credentials.ts#savePlatformCredentials }
  - { kind: doc, role: intent, target: docs/oauth-apps.md, title: "OAuth apps" }
---

# Set up a platform app

Enter the client id and secret of the Admin's own LinkedIn, Threads or X developer app in the accounts dialog, and connect straight away. The secret is stored encrypted and never shown again.
