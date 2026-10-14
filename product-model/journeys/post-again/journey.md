---
actors: [admin]
references:
  - { kind: code, role: implementation, target: src/routes/posts/+page.svelte }
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#duplicateDraft }
---

# Post again

## Goal

The Admin sends something they already wrote once more, as a new post.

## Success criterion

A copy of the post is open in the composer, ready to publish or schedule.
