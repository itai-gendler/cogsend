---
availability:
  - { place: web::app }
domain: compose
references:
  - { kind: code, role: implementation, target: src/lib/components/XQuoteCard.svelte }
  - { kind: code, role: implementation, target: src/lib/domain/x-quote.ts }
  - { kind: code, role: implementation, target: src/routes/posts/+page.svelte }
  - { kind: doc, role: intent, target: docs/composer.md, title: "Quote posts on X" }
---

# Quote an X post

Make a card quote an X post: X shows a post as a quote when its text ends with a link to another X post. The composer draws the link as a quote card; it can be pasted, picked from the Admin's recent published X posts, or started from a published post in Posts.
