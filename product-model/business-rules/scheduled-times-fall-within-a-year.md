---
appliesTo:
  - { type: capability, id: schedule-post }
  - { type: capability, id: reschedule-delivery }
references:
  - { kind: code, role: implementation, target: src/lib/domain/request-limits.ts#runAtError }
---

# A scheduled time is in the future and within the next year

Scheduling or rescheduling refuses a time in the past or more than a year ahead.
