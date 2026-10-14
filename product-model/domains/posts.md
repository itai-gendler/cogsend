---
references:
  - { kind: code, role: implementation, target: src/routes/posts/+page.svelte }
  - { kind: doc, role: intent, target: docs/posts.md, title: Posts and Insights }
---

# Posts

Everything written and what happened to it: finding a post, opening it, and
acting on its deliveries once they are scheduled or have failed.

## Boundary

Owns browsing posts and rescheduling or retrying their deliveries. It does not
own writing or changing a post's content, which belongs to Compose, nor the
trends over time shown in Insights.
