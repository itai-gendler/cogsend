---
appliesTo:
  - { type: capability, id: write-post }
  - { type: capability, id: change-new-post-defaults-settings }
  - { type: entity, id: admin, facts: [Preselected accounts, Default Mastodon visibility] }
references:
  - { kind: code, role: implementation, target: src/lib/domain/profile-settings.ts }
  - { kind: code, role: implementation, target: src/lib/server/draft-record.ts }
---

# A new post starts from the new post defaults

A post started in the composer has the Admin's preselected accounts ticked, or every active account when none is preselected, and their default Mastodon visibility.
