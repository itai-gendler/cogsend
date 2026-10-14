---
kind: system
acts: external
references:
  - { kind: doc, role: intent, target: docs/scheduling.md, title: Scheduling }
  - { kind: code, role: implementation, target: src/routes/api/internal/tick/+server.ts }
---

# External cron

A service outside the Worker, such as cron-job.org, a systemd timer or the
bundled GitHub Actions workflow, that calls the tick so scheduled posts go out
when the instance's own cron trigger is not available.
