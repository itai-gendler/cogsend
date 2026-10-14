---
references:
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
  - { kind: doc, role: intent, target: docs/composer.md, title: Writing and publishing }
---

# Compose

Writing one post: its thread of cards, images and alt text, the tab per
platform, the accounts it goes to, and sending it now or at a set time.

## Boundary

Owns a post's content and choosing when it goes out from the composer. It does
not own what happens to deliveries already scheduled or sent, which belongs to
Posts, nor connecting the accounts a post can go to, which belongs to Accounts.
