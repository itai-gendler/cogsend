---
singleton: true
references:
  - { kind: code, role: implementation, target: src/lib/server/app-settings.ts }
  - { kind: code, role: implementation, target: src/lib/server/env.ts }
  - { kind: code, role: implementation, target: src/lib/server/scheduler.ts#writeHeartbeat }
  - { kind: doc, role: intent, target: docs/configuration.md, title: Configuration }
---

# Instance

The deployment itself, kept once: what it is called, what its operator set up
for it outside the app, and how its scheduled publishing is doing.

## Information kept

- **Name** — shown in the page title, the header and the login screen; CogSend when empty; up to 60 characters
- **Encryption key** — the key the instance was deployed with; it encrypts stored credentials and proves who may create the account
- **Offer pre-releases** — whether release candidates are offered as updates too
- **Last tick** — when a tick last ran
- **Call budget** — how many calls one request may make to the database, the media bucket and the platforms; 50 unless the operator raised it for a paid plan
- **Failure email** — the address failure digests go to, when the operator set up email sending
- **Last failure digest** — when the last failure digest went out
- **Video uploads** — whether the operator turned video uploads on
