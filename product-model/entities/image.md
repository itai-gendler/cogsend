---
references:
  - { kind: code, role: implementation, target: src/lib/server/db/schema.ts#draftMedia }
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/media/+server.ts" }
  - { kind: code, role: implementation, target: src/lib/domain/media-limits.ts }
  - { kind: doc, role: intent, target: docs/composer.md, title: Images and alt text }
---

# Image

An image attached to one card of a post, or a video while the operator has
video uploads on.

## Information kept

- **Card** — the thread card it belongs to
- **Order** — its place among the card's images
- **Alt text** — the description that goes out with it on platforms that support one
- **Format** — JPEG, PNG, WebP or GIF, or MP4 video
- **Size** — its size in bytes, checked against each platform's limit
- **Dimensions** — its width and height
