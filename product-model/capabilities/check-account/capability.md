---
availability:
  - { place: web::app }
domain: accounts
references:
  - { kind: code, role: implementation, target: "src/routes/api/connections/[id]/verify/+server.ts" }
  - { kind: doc, role: intent, target: docs/zernio.md, title: "Reconnecting and checking" }
---

# Check an account

Ask the platform, or Zernio, whether an account still works, and mark it active again or as needing reconnection.
