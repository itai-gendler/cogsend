---
appliesTo:
  - { type: capability, id: attach-image }
  - { type: entity, id: image, facts: [Card] }
references:
  - { kind: code, role: implementation, target: src/lib/domain/media-limits.ts }
  - { kind: code, role: implementation, target: "src/routes/api/drafts/[id]/media/+server.ts" }
---

# A card carries at most four images

Each card of a thread takes up to four images, a post up to 32 files across its cards and the Admin up to 1,000 files in all; a video cannot share a card with images.
