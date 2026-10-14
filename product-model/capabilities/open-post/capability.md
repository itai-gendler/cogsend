---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: posts
references:
  - { kind: code, role: implementation, target: src/routes/compose/+page.server.ts }
  - { kind: code, role: implementation, target: src/lib/server/draft-record.ts#loadOwnedDraft }
  - { kind: code, role: implementation, target: src/lib/components/PostStatusBanner.svelte }
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/+server.ts" }
---

# Open a post

Open one post with everything it holds. From Posts, Edit Post opens it in the composer, which shows above the text when and where it goes out; a post published to every account opens read-only.
