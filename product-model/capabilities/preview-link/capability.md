---
availability:
  - { place: web::app }
domain: compose
references:
  - { kind: code, role: implementation, target: src/routes/api/link-preview/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/opengraph.ts#fetchOpenGraph }
  - { kind: code, role: implementation, target: src/lib/components/LinkPreview.svelte }
---

# Preview a link

See the link preview a URL in a card will produce, while writing.
