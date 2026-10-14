---
availability:
  - { place: web::app }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
  - { kind: code, role: implementation, target: src/lib/domain/profile-settings.ts }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Global, and a tab per platform" }
---

# Change Mastodon options

Set how a post appears on Mastodon: its visibility and an optional content warning. New posts start with the Admin's default visibility.
