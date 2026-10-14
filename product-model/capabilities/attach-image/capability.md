---
availability:
  - { place: web::app }
  - { place: api }
domain: compose
references:
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/media/+server.ts" }
  - { kind: code, role: implementation, target: src/lib/components/shrink-image.ts }
  - { kind: code, role: implementation, target: src/lib/domain/media-limits.ts }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Images and alt text" }
---

# Attach an image

Add an image to one card of a post, up to four per card. An image over 2 MB is shrunk in the browser first; a video is accepted only while the operator has video uploads on.
