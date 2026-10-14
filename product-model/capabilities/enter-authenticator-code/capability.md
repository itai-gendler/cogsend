---
availability:
  - { place: web::login }
references:
  - { kind: code, role: implementation, target: src/lib/server/totp.ts#verifyMfa }
  - { kind: code, role: implementation, target: src/routes/login/verify/+page.svelte }
---

# Enter an authenticator code

Finish signing in with a six-digit code from the authenticator app, or with
one unused backup code.
