---
entities:
  - { entity: account, shows: [Platform, Handle, Display name, Avatar, Connected through], collects: [Server, Handle, Credentials, Zernio API key] }
  - { entity: platform-app, shows: [Platform, Client ID, Source], collects: [Client ID, Client secret] }
entryPoints:
  - web: /accounts
references:
  - { kind: code, role: implementation, target: src/routes/accounts/+page.svelte }
---

# Accounts

The connected accounts, each with its state, and the platform picker that
connects another, directly or through Zernio.
