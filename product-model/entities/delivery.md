---
references:
  - { kind: code, role: implementation, target: src/lib/server/db/schema.ts#publishTargets }
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#publishTarget }
  - { kind: code, role: implementation, target: src/lib/domain/post-state.ts#summarizePost }
  - { kind: doc, role: intent, target: docs/posts.md, title: Posts }
---

# Delivery

One post going to one account: when it goes, how it went and where it landed.
A post sent to five accounts has five deliveries, each with its own result.

## Information kept

- **Scheduled time** — when it is due; empty when it goes out straight away
- **Attempts** — how many times it has been tried since it was last rescheduled or retried
- **Error** — why its last attempt failed
- **Link** — the address of the published post on the platform

## States

### Queued

Due straight away: sent from the composer or the API and waiting for its turn
in this request or the next tick.

### Scheduled

Waiting for its scheduled time.

### Retrying

Failed with something temporary, such as a rate limit or a platform timeout,
and waiting to try again on its own.

### Publishing

Being sent right now; the post cannot be edited until the result is in.

### Published

Accepted by the platform.

### Failed

Stopped: refused for good, or out of automatic attempts. It waits for a manual
retry.

### Cancelled

Taken off the schedule; it will not go out unless retried.
