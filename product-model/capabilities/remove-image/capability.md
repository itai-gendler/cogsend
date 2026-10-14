---
availability:
  - { place: web::app }
  - { place: api }
domain: compose
references:
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/media/+server.ts" }
---

# Remove an image

Take an image off a card and delete its file.
