---
actors: [admin]
access: public
entryPoints:
  - web: /login
references:
  - { kind: code, role: implementation, target: src/routes/login/+page.svelte }
  - { kind: code, role: implementation, target: src/routes/login/setup-2fa/+page.svelte }
  - { kind: code, role: implementation, target: src/routes/login/verify/+page.svelte }
---

# Login

Where the Admin arrives before signing in: creating the account on a fresh
instance, signing in, and setting up or entering the second factor.
