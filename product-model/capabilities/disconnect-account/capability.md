---
availability:
  - { place: web::app }
domain: accounts
references:
  - { kind: code, role: implementation, target: "src/routes/api/connections/[id]/+server.ts" }
  - { kind: code, role: implementation, target: src/routes/accounts/+page.svelte }
  - { kind: doc, role: intent, target: docs/accounts.md, title: "Disconnecting" }
---

# Disconnect an account

Stop posting to an account. Its scheduled deliveries are removed, posts left with nothing to send return to Drafts, and what it already published is kept: an account with published history is archived so Insights still counts it, and one without is removed.
