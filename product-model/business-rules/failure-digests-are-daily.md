---
appliesTo:
  - { type: capability, id: send-failure-digest }
  - { type: entity, id: instance, facts: [Last failure digest] }
references:
  - { kind: code, role: implementation, target: src/lib/server/scheduler.ts#maybeSendFailureDigest }
---

# A failure digest goes out at most once a day

A digest is sent only while the operator set up email sending, at most once in 24 hours, listing deliveries that failed since the last one and never those still retrying.
