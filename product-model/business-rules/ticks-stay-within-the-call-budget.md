---
appliesTo:
  - { type: capability, id: publish-due-posts }
  - { type: capability, id: publish-post }
  - { type: entity, id: instance, facts: [Call budget] }
references:
  - { kind: code, role: implementation, target: src/lib/server/budget.ts }
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#publishCallEstimate }
  - { kind: doc, role: intent, target: docs/scheduling.md, title: "How a tick works" }
---

# A tick or a publish request starts only what its call budget can finish

The first due delivery always runs; each further one starts only if its estimated calls fit in what is left of the request's budget, and the rest stay due for the next tick.

## Rationale

A request that runs out after a platform accepted a post would leave it to be sent again.
