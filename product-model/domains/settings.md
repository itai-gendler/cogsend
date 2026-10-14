---
references:
  - { kind: code, role: implementation, target: src/routes/settings/+page.svelte }
  - { kind: doc, role: intent, target: docs/configuration.md, title: Configuration }
---

# Settings

The Admin's profile, the defaults new posts start with, API access, the
authenticator, the credential an external cron uses, the instance's name and
the login.

## Boundary

Owns the Admin's own settings, keys and login and the instance's name. It does
not own connected accounts or platform apps, which belong to Accounts, nor
signing in itself.
