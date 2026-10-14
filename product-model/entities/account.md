---
relations:
  - { entity: delivery, verb: receives, cardinality: one-to-many }
references:
  - { kind: code, role: implementation, target: src/lib/server/db/schema.ts#connections }
  - { kind: code, role: implementation, target: src/lib/server/connection-list.ts }
  - { kind: doc, role: intent, target: docs/accounts.md, title: Connecting accounts }
---

# Account

A social account the Admin connected, on Mastodon, Bluesky, LinkedIn, Threads
or X, directly or through Zernio. Posts are delivered to accounts.

## Information kept

- **Platform** — Mastodon, Bluesky, LinkedIn, Threads or X
- **Handle** — the account's handle on its platform
- **Display name** — the name it shows on its platform
- **Avatar** — its profile picture
- **Server** — the Mastodon server or Bluesky host it lives on
- **Connected through** — directly, or through Zernio
- **Credentials** — the token or Bluesky app password the Product posts with, kept encrypted
- **Zernio API key** — the Zernio key an account connected through Zernio publishes with, kept encrypted
- **Character limit** — the character limit its Mastodon server sets

## States

### Active

Its credentials work and posts are delivered to it.

### Needs reconnect

Its platform stopped accepting its credentials; it is marked in Accounts and
in the composer until it is reconnected or checked again.

### Archived

Disconnected while it still has published history: its credentials are gone,
nothing more is delivered to it, and its history still counts in Insights.
