---
availability:
  - { place: web::app }
domain: settings
references:
  - { kind: code, role: implementation, target: src/routes/api/account/+server.ts }
  - { kind: code, role: implementation, target: src/lib/domain/credentials.ts#passwordProblem }
  - { kind: doc, role: intent, target: docs/configuration.md, title: "The login" }
---

# Change login settings

Change the email or the password used to sign in, under Settings, Login, after entering the current password. A new password signs every device out.
