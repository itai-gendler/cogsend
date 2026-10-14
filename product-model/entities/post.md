---
relations:
  - { entity: platform-override, verb: has, cardinality: one-to-many }
  - { entity: image, verb: has, cardinality: one-to-many }
  - { entity: delivery, verb: has, cardinality: one-to-many }
references:
  - { kind: code, role: implementation, target: src/lib/server/db/schema.ts#drafts }
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#refreshDraftStatus }
  - { kind: code, role: implementation, target: src/lib/domain/thread-segments.ts }
  - { kind: doc, role: intent, target: docs/composer.md, title: Writing and publishing }
---

# Post

What the Admin writes once and sends to one or more accounts: a thread of
cards, optionally tailored per platform, with images. Where it stands follows
from its deliveries.

## Information kept

- **Title** — an optional title, set through the API
- **Text** — the Global text every account gets unless its platform has an override; thread cards are separated by a line holding only ---
- **Selected accounts** — the accounts ticked for it in the composer
- **Last edited** — when it last changed

## States

### Draft

Not sent anywhere and not waiting to be: newly written, unscheduled, or left
with no deliveries.

### Scheduled

Waiting to go out to its accounts, at a set time or straight away.

### Partly published

Its deliveries ended differently: published on some accounts while others
failed or still wait, or failed on some while others still wait.

### Published

Published on every account it was sent to.

### Failed

Failed on every account it was sent to.
