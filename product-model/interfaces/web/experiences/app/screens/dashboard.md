---
entities:
  - { entity: admin, shows: [Display name] }
  - { entity: instance, shows: [Last tick] }
  - { entity: delivery, shows: [Scheduled time, Error] }
entryPoints:
  - web: /
references:
  - { kind: code, role: implementation, target: src/routes/+page.svelte }
  - { kind: code, role: implementation, target: src/routes/+page.server.ts }
---

# Dashboard

The home page: a greeting, whether publishing is healthy, how many posts are
drafts, scheduled or failed, and a way to start writing.
