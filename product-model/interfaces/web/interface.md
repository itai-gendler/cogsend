---
type: web
actors: [admin]
entryPoints:
  - web: /
references:
  - { kind: code, role: implementation, target: src/routes/+layout.svelte }
  - { kind: code, role: implementation, target: src/hooks.server.ts }
---

# CogSend web app

The browser app on the instance's own address, where the Admin signs in,
writes and schedules posts, follows what happened to them and runs the
instance.
