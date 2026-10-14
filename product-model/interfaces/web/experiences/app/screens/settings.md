---
entities:
  - { entity: admin, shows: [Email, Display name, Profile picture, Default Mastodon visibility, Preselected accounts, Backup codes, Authenticator], collects: [Display name, Profile picture, Default Mastodon visibility, Preselected accounts, Email, Password] }
  - { entity: api-key, shows: [Prefix, Scope, Created, Last used], collects: [Scope] }
  - { entity: tick-token, shows: [Prefix, Created] }
  - { entity: instance, shows: [Name, Last tick, Offer pre-releases], collects: [Name, Offer pre-releases] }
  - { entity: account, shows: [Platform, Display name] }
entryPoints:
  - web: /settings
references:
  - { kind: code, role: implementation, target: src/routes/settings/+page.svelte }
---

# Settings

The Admin's settings page: Profile Details, New post defaults, API access,
Two-factor authentication, Scheduled publishing, Instance and Login.
