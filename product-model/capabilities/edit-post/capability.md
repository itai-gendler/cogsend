---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#updateDraft }
  - { kind: code, role: implementation, target: src/lib/server/publish-plan.ts#draftEditBlock }
  - { kind: code, role: implementation, target: src/lib/components/compose-session.svelte.ts }
  - { kind: code, role: implementation, target: src/lib/domain/text-split.ts }
  - { kind: doc, role: intent, target: docs/composer.md, title: "A thread is a list of cards" }
---

# Edit a post

Change a post's text and thread cards. The composer saves as the Admin types and retries a failed save on its own; scripts and agents send the change. A post being sent, or already published to every account, cannot be changed.
