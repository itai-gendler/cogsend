---
appliesTo:
  - { type: capability, id: edit-post }
  - { type: capability, id: select-account }
references:
  - { kind: code, role: implementation, target: src/lib/domain/validation/text.ts }
  - { kind: code, role: implementation, target: src/lib/domain/editor-limits.ts }
  - { kind: doc, role: intent, target: docs/composer.md, title: "A thread is a list of cards" }
---

# A card is counted against the strictest limit among the ticked accounts

The character counter and the automatic split use the smallest limit among the accounts a post goes to, counted the way that platform counts: graphemes for most, every link as 23 characters on Mastodon and X, and CJK characters and each emoji as two on X.
