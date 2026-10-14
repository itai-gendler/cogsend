---
availability:
  - { place: web::login }
references:
  - { kind: code, role: implementation, target: src/routes/api/auth/login/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/auth-gate.ts#assertPasswordGateOpen }
  - { kind: code, role: implementation, target: src/routes/login/+page.svelte }
---

# Sign in

Sign in with the account's email and password. A correct password leads to the
second factor: entering a code, or setting up an authenticator the first time.
