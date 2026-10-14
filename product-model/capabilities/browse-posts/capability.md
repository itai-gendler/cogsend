---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: posts
references:
  - { kind: code, role: implementation, target: src/routes/posts/+page.svelte }
  - { kind: code, role: implementation, target: src/lib/server/post-list.ts#loadQueueList }
  - { kind: code, role: implementation, target: src/lib/server/post-list.ts#loadDraftSummaries }
  - { kind: code, role: implementation, target: src/routes/api/queue/+server.ts }
  - { kind: doc, role: intent, target: docs/posts.md, title: "Posts" }
---

# Browse posts

See everything written and what happened to it: one card per post with a result per account, in the tabs All Posts, Scheduled, Published, Failed and Drafts, narrowed to one account or by a search of the text. Scripts and agents list drafts and the publish queue.
