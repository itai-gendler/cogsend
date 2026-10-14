---
entities:
  - { entity: admin, collects: [Authenticator, Backup codes] }
entryPoints:
  - web: /login/verify
references:
  - { kind: code, role: implementation, target: src/routes/login/verify/+page.svelte }
---

# Enter code

The second step of signing in: a six-digit code from the authenticator app, or
one unused backup code.
