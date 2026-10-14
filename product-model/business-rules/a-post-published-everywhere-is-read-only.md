---
appliesTo:
  - { type: capability, id: edit-post }
  - { type: capability, id: add-platform-override }
  - { type: capability, id: edit-platform-override }
  - { type: capability, id: remove-platform-override }
  - { type: capability, id: attach-image }
  - { type: capability, id: edit-alt-text }
  - { type: capability, id: remove-image }
  - { type: entity, id: post }
references:
  - { kind: code, role: implementation, target: src/lib/domain/published-lock.ts#isFullyPublished }
  - { kind: code, role: implementation, target: src/lib/server/publish-plan.ts#draftEditBlock }
---

# A post published to every account is never edited

Once every delivery of a post that is not cancelled has gone out, its text, overrides and images no longer change; it opens read-only and is duplicated to post again. A post that failed on some accounts stays editable.

## Rationale

Editing would only rewrite the record of what went out, not the posts themselves.
