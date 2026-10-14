---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#setDraftVariant }
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/variants/+server.ts" }
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Global, and a tab per platform" }
---

# Add a platform override

Give one platform its own text for a post, in a tab of its own beside Global. In the composer this is Add override… with more than one account ticked; scripts and agents set it for a platform that has none.
