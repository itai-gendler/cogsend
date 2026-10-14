---
availability:
  - { place: web::login }
references:
  - { kind: code, role: implementation, target: src/lib/server/totp.ts#enrollStart }
  - { kind: code, role: implementation, target: src/lib/server/totp.ts#enrollConfirm }
  - { kind: code, role: implementation, target: src/routes/login/setup-2fa/+page.svelte }
---

# Set up two-factor authentication

Enroll an authenticator app while signing in: scan the QR code, save the ten
backup codes, and confirm with the first code. Signing in finishes once it is
confirmed.
