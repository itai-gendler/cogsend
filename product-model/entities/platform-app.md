---
references:
  - { kind: code, role: implementation, target: src/lib/server/platform-credentials.ts }
  - { kind: code, role: implementation, target: "src/routes/api/settings/platform-apps/[platform]/+server.ts" }
  - { kind: doc, role: intent, target: docs/oauth-apps.md, title: OAuth apps }
---

# Platform app

The developer app of the Admin's own that LinkedIn, Threads or X require
before an account on that platform can be connected directly.

## Information kept

- **Platform** — LinkedIn, Threads or X
- **Client ID** — the app's client id
- **Client secret** — the app's secret, kept encrypted and never shown again
- **Source** — entered in the accounts dialog, or set by the operator as Worker secrets, which take precedence
