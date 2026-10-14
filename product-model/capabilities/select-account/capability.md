---
availability:
  - { place: web::app }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Choosing destinations" }
---

# Tick an account for a post

Add a connected account to the accounts a post goes to, from the account list in the composer.
