---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#deleteDraft }
  - { kind: code, role: implementation, target: src/routes/posts/+page.svelte }
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
---

# Delete a post

Delete a post with its overrides, images and deliveries: Remove on a draft card, the bin in the composer, or a delete through the API. A scheduled post deleted this way is never published; what already went out stays on the platforms.
