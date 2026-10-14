---
references:
  - { kind: code, role: implementation, target: src/lib/server/db/schema.ts#draftVariants }
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#setDraftVariant }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Global, and a tab per platform" }
---

# Platform override

A post's own version for one platform, written in that platform's tab instead
of the Global text, and the Mastodon options a post carries.

## Information kept

- **Platform** — the platform it is for
- **Text** — that platform's own text and thread cards
- **Visibility** — on Mastodon, Public, Unlisted, Followers or Direct
- **Content warning** — on Mastodon, an optional content warning
