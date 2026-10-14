---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#scheduleDraft }
  - { kind: code, role: implementation, target: src/lib/domain/request-limits.ts#runAtError }
  - { kind: code, role: implementation, target: src/lib/domain/post-state.ts#selectionDrift }
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Publish now, or schedule" }
---

# Schedule a post

Set a post to go out at a time, one delivery per account. In the composer the time is an offset (one hour by default) or a specific date and time in the Admin's own time zone, and scheduling goes to exactly the accounts ticked; scripts and agents add the accounts they name.
