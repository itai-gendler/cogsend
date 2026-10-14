---
appliesTo:
  - { type: capability, id: publish-post }
  - { type: capability, id: publish-due-posts }
references:
  - { kind: code, role: implementation, target: src/lib/domain/thread-segments.ts }
  - { kind: code, role: implementation, target: src/lib/server/providers/linkedin.ts }
---

# LinkedIn gets a thread as one post

LinkedIn has no threads: a thread sent there is flattened into one post with its cards joined by a blank line.
