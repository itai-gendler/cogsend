---
availability:
  - { place: web::app }
domain: settings
references:
  - { kind: code, role: implementation, target: src/routes/api/settings/+server.ts }
  - { kind: code, role: implementation, target: src/lib/domain/profile-settings.ts }
  - { kind: code, role: implementation, target: src/routes/settings/+page.svelte }
---

# Change new post defaults

Choose what new posts start with under Settings, New post defaults: the Mastodon visibility and the preselected accounts. Posts already written keep their own.
