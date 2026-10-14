---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#setDraftVariant }
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
---

# Edit a platform override

Change the text a post sends to one platform, in that platform's tab, without touching Global or the other platforms.
