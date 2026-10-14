---
actors: [admin]
access: authenticated
entryPoints:
  - web: /
references:
  - { kind: code, role: implementation, target: src/routes/+layout.svelte }
  - { kind: code, role: implementation, target: src/lib/server/require.ts#requireUser }
---

# App

Everything the signed-in Admin does once both factors are checked: composing,
posts, insights, accounts and settings.
