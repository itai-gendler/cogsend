---
availability:
  - { place: web::app }
references:
  - { kind: code, role: implementation, target: src/lib/server/scheduler.ts#maybeSendFailureDigest }
  - { kind: doc, role: intent, target: docs/scheduling.md, title: "Failure alerts (optional)" }
---

# Send a failure digest

After a tick, email the operator's failure address a list of posts that failed since the last digest, at most once a day. It exists only while the operator set up email sending.
