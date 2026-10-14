---
availability:
  - { place: api }
  - { place: mcp }
references:
  - { kind: code, role: implementation, target: src/lib/server/api/operations.ts#validatePost }
  - { kind: code, role: implementation, target: src/routes/api/validate/+server.ts }
  - { kind: code, role: implementation, target: src/lib/domain/validation/text.ts }
---

# Check a post against platform limits

Check a text against every platform's limits, counted the way each platform counts, before saving or publishing it.
