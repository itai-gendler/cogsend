---
kind: system
acts: external
references:
  - { kind: doc, role: intent, target: docs/api.md, title: API }
  - { kind: code, role: implementation, target: src/hooks.server.ts }
---

# API client

A script, Shortcut or cron job the Admin runs that calls the API with their
personal API key instead of signing in. It acts as the Admin on posts and
their deliveries, within what the key's scope allows, and never on accounts,
keys or the login.
