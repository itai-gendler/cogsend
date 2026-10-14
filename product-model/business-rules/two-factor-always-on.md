---
appliesTo:
  - { type: capability, id: enter-authenticator-code }
  - { type: capability, id: set-up-two-factor-authentication }
  - { type: capability, id: replace-authenticator }
references:
  - { kind: code, role: implementation, target: src/lib/server/auth.ts#isFullyVerified }
  - { kind: code, role: implementation, target: src/routes/settings/+page.svelte }
---

# Two-factor authentication is always on

Every sign-in needs a code from the authenticator or an unused backup code, and there is no way to turn it off; it can only be replaced.
