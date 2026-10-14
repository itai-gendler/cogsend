---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#deleteDraftVariant }
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
---

# Remove a platform override

Send a platform the Global text again. In the composer this is the re-sync button on an unlinked tab; scripts and agents delete the override.
