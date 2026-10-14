---
references:
  - { kind: code, role: implementation, target: src/routes/accounts/+page.svelte }
  - { kind: doc, role: intent, target: docs/accounts.md, title: Connecting accounts }
---

# Accounts

The social accounts posts go to: connecting them directly or through Zernio,
checking and reconnecting them, disconnecting them, and the developer apps some
platforms need first.

## Boundary

Owns connected accounts and platform apps. It does not own choosing which
accounts one post goes to, which belongs to Compose, nor the personal API key,
which belongs to Settings.
