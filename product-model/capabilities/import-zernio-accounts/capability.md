---
availability:
  - { place: web::app }
domain: accounts
references:
  - { kind: code, role: implementation, target: src/routes/api/connections/zernio/accounts/+server.ts }
  - { kind: code, role: implementation, target: src/routes/api/connections/zernio/import/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/zernio-import.ts#upsertZernioConnection }
  - { kind: doc, role: intent, target: docs/zernio.md, title: "Import accounts you already have in Zernio" }
---

# Import Zernio accounts

Bring accounts the Admin already has in Zernio into CogSend with a Zernio key: show the Zernio accounts, tick some and import them.
