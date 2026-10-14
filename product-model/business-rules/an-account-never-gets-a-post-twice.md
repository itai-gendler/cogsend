---
appliesTo:
  - { type: capability, id: publish-post }
  - { type: capability, id: schedule-post }
  - { type: capability, id: retry-delivery }
  - { type: capability, id: publish-due-posts }
references:
  - { kind: code, role: implementation, target: src/lib/server/publish-plan.ts#classifyWinner }
  - { kind: code, role: implementation, target: src/lib/server/publish.ts#publishTarget }
  - { kind: doc, role: intent, target: docs/api.md, title: "Publishing behaviour" }
---

# An account never receives the same post twice

Publishing, scheduling or retrying for an account whose delivery already went out sends nothing; a delivery being sent is never claimed a second time, and a thread that failed half-way resumes after the cards that went out.
