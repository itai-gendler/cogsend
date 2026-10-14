---
availability:
  - { place: web::app }
domain: accounts
references:
  - { kind: code, role: implementation, target: src/lib/server/oauth-callback.ts#createOAuthCallback }
  - { kind: code, role: implementation, target: src/routes/api/connections/mastodon/+server.ts }
  - { kind: code, role: implementation, target: src/routes/api/connections/bluesky/+server.ts }
  - { kind: code, role: implementation, target: src/routes/api/connections/x/+server.ts }
  - { kind: code, role: implementation, target: src/routes/api/connections/zernio/connect/+server.ts }
  - { kind: code, role: implementation, target: src/routes/api/connections/zernio/callback/+server.ts }
  - { kind: doc, role: intent, target: docs/accounts.md, title: "Connecting accounts" }
  - { kind: doc, role: intent, target: docs/zernio.md, title: "Connect through Zernio" }
---

# Connect an account

Connect a Mastodon, Bluesky, LinkedIn, Threads or X account from Connect new, directly or through Zernio. Mastodon and Bluesky work straight away; LinkedIn, Threads and X connect directly only once a platform app is set up for them. Reconnect runs the same flow for an account that needs it and keeps its history.
