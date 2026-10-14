---
appliesTo:
  - { type: capability, id: publish-due-posts }
  - { type: capability, id: publish-post }
  - { type: entity, id: delivery, facts: [Attempts] }
references:
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#retryDelayMs }
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#isRetryableError }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Publish now, or schedule" }
---

# A temporary failure retries on its own, five attempts in all

A rate limit, a timeout or another failure retrying can fix sets the next attempt one minute later, doubling up to thirty minutes, until five attempts have been made; then the delivery is failed. A manual retry or reschedule starts the count afresh.
