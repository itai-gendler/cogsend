---
availability:
  - { place: web::login }
references:
  - { kind: code, role: implementation, target: src/routes/api/auth/claim/+server.ts }
  - { kind: code, role: implementation, target: src/routes/login/+page.svelte }
  - { kind: doc, role: intent, target: docs/configuration.md, title: The login }
---

# Create the account

Create the instance's one account from the login page of a fresh instance, by
entering the encryption key the instance was deployed with, an email and a
password. Once the account exists the form is gone.
