---
appliesTo:
  - { type: capability, id: publish-due-posts }
  - { type: capability, id: retry-delivery }
references:
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#isRetryableError }
  - { kind: doc, role: intent, target: docs/api.md, title: "Publishing behaviour" }
---

# A post that may already be live is never retried on its own

When X, LinkedIn or Threads got the request that creates a post but no answer came back, the delivery fails saying the post may have been published, and only a manual retry sends it again.

## Rationale

Those platforms accept no key that would let them recognise a repeated request, so an automatic retry could post twice.
