---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#publishDraft }
  - { kind: code, role: implementation, target: src/lib/server/publish-plan.ts#ensureTargets }
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#publishTarget }
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/publish/+server.ts" }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Publish now, or schedule" }
  - { kind: doc, role: intent, target: docs/api.md, title: "Publishing behaviour" }
---

# Publish a post

Send a post now to each of its accounts, one delivery per account, and see the result for each. In the composer Publish asks for confirmation unless the Admin turned that off in this browser; scripts and agents name the accounts. An account that already has the post is skipped, and accounts beyond what one request can afford wait for the next tick.
