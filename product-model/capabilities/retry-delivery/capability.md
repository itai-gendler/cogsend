---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: posts
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#retryDelivery }
  - { kind: code, role: implementation, target: src/routes/api/targets/bulk/+server.ts }
  - { kind: code, role: implementation, target: src/routes/posts/+page.svelte }
  - { kind: doc, role: intent, target: docs/posts.md, title: "Posts" }
---

# Retry a delivery

Send a failed delivery again now. Retry on a failed card retries only the accounts that failed; a retry starts the automatic attempts afresh.
