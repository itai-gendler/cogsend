---
entities:
  - { entity: post, shows: [Text, Selected accounts, Last edited], collects: [Text, Selected accounts] }
  - { entity: platform-override, shows: [Platform, Text, Visibility, Content warning], collects: [Text, Visibility, Content warning] }
  - { entity: image, shows: [Card, Order, Alt text], collects: [Alt text] }
  - { entity: account, shows: [Platform, Handle, Display name, Avatar] }
  - { entity: delivery, shows: [Scheduled time, Error, Link], collects: [Scheduled time] }
entryPoints:
  - web: /compose
references:
  - { kind: code, role: implementation, target: src/routes/compose/+page.svelte }
  - { kind: code, role: implementation, target: src/lib/components/Editor.svelte }
  - { kind: code, role: implementation, target: src/lib/components/PostStatusBanner.svelte }
---

# Composer

One post being written: its thread of cards and their images, a tab per
platform, the accounts it goes to, and where it stands once it is scheduled or
sent.
