---
actors: [admin]
references:
  - { kind: code, role: implementation, target: src/routes/api/auth/claim/+server.ts }
  - { kind: code, role: implementation, target: src/routes/login/setup-2fa/+page.svelte }
---

# Claim a fresh instance

## Goal

The person who deployed an instance makes it theirs and gets into it with two-factor authentication on.

## Success criterion

The Admin exists with an authenticator enrolled and is in the app.
