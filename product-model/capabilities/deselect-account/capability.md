---
availability:
  - { place: web::app }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Choosing destinations" }
---

# Untick an account for a post

Take an account off the accounts a post goes to, one at a time or all at once with Clear all.
