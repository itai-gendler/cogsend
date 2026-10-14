---
availability:
  - { place: web::app }
  - { place: api }
domain: compose
references:
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/media/+server.ts" }
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
---

# Edit alt text

Describe an image; the description goes out with it on platforms that support alt text.
