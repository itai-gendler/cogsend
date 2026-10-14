---
entities:
  - { entity: admin, collects: [Email, Password] }
  - { entity: instance, shows: [Name], collects: [Encryption key] }
entryPoints:
  - web: /login
references:
  - { kind: code, role: implementation, target: src/routes/login/+page.svelte }
  - { kind: code, role: implementation, target: src/routes/login/+page.server.ts }
---

# Sign in

The login page. On an instance that has no account yet it asks for the
deployment's encryption key, an email and a password to create one; afterwards
it asks for the email and password.
