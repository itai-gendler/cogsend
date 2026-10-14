---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#duplicateDraft }
  - { kind: code, role: implementation, target: src/routes/posts/+page.svelte }
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/duplicate/+server.ts" }
---

# Duplicate a post

Copy a post into a new draft with its overrides and copies of its images, but none of its deliveries; Post again on a published card and Duplicate to post again in the composer do the same. In the app the copy opens in the composer.
