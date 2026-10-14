---
entities:
  - { entity: admin, shows: [Authenticator, Backup codes] }
entryPoints:
  - web: /login/setup-2fa
references:
  - { kind: code, role: implementation, target: src/routes/login/setup-2fa/+page.svelte }
---

# Set up authenticator

Where the Admin enrolls an authenticator app the first time they sign in: a
QR code and the key behind it, the backup codes to save, and the first code to
confirm.
