---
availability:
  - { place: web::app }
domain: settings
references:
  - { kind: code, role: implementation, target: src/routes/api/auth/totp/rotate/start/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/totp.ts#rotateStart }
  - { kind: code, role: implementation, target: src/lib/server/totp.ts#enrollConfirm }
---

# Replace the authenticator

Move two-factor authentication to a new authenticator app with fresh backup codes, under Settings, Two-factor authentication, after proving the current one. It can be replaced but never turned off.
