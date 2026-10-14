---
appliesTo:
  - { type: capability, id: delete-post }
  - { type: capability, id: disconnect-account }
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#deleteDraft }
  - { kind: doc, role: intent, target: docs/zernio.md, title: "Reconnecting and checking" }
---

# Deleting in CogSend never deletes from a platform

Deleting a post or disconnecting an account changes only what CogSend keeps; anything already published stays on its platform, and an account stays in Zernio.
