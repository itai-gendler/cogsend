---
entities:
  - { entity: post, shows: [Text, Last edited] }
  - { entity: delivery, shows: [Scheduled time, Error, Link], collects: [Scheduled time] }
  - { entity: account, shows: [Platform, Handle, Avatar] }
entryPoints:
  - web: /posts
references:
  - { kind: code, role: implementation, target: src/routes/posts/+page.svelte }
  - { kind: code, role: implementation, target: src/lib/server/post-list.ts }
---

# Posts

Everything the Admin has written and what happened to it, one card per post
with a result per account, in the tabs All Posts, Scheduled, Published, Failed
and Drafts.
