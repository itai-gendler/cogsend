---
entities:
  - { entity: delivery, shows: [Scheduled time, Error] }
  - { entity: account, shows: [Platform, Handle] }
entryPoints:
  - web: /insights
references:
  - { kind: code, role: implementation, target: src/routes/insights/+page.svelte }
  - { kind: code, role: implementation, target: src/lib/server/insights-report.ts }
---

# Insights

How publishing has gone over the last 7, 30 or 90 days, against the period
before.
