---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#createDraft }
  - { kind: code, role: implementation, target: src/routes/compose/+page.server.ts }
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
  - { kind: code, role: implementation, target: src/routes/api/drafts/+server.ts }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Drafts save themselves" }
---

# Write a post

Start a new post. In the composer it is saved as a draft as soon as it has something in it, starting with the Admin's new post defaults; through the API or the MCP server it is created in one call.
