---
availability:
  - { place: web::app }
  - { place: api }
references:
  - { kind: code, role: implementation, target: src/lib/server/insights-report.ts#loadInsights }
  - { kind: code, role: implementation, target: src/routes/insights/+page.svelte }
  - { kind: code, role: implementation, target: src/routes/api/insights/+server.ts }
  - { kind: code, role: implementation, target: src/lib/domain/insights.ts }
  - { kind: doc, role: intent, target: docs/posts.md, title: "Insights" }
---

# View insights

See how publishing has gone over the last 7, 30 or 90 days against the period before, counted in the Admin's own days: published and scheduled counts, the last post, a chart per day, failures grouped by reason, and a row per account, archived ones included.
