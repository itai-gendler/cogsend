---
availability:
  - { place: web::app }
  - { place: api }
  - { place: mcp }
domain: accounts
references:
  - { kind: code, role: implementation, target: src/lib/server/connection-list.ts#listConnections }
  - { kind: code, role: implementation, target: src/routes/accounts/+page.svelte }
  - { kind: code, role: implementation, target: src/routes/api/connections/+server.ts }
---

# Browse accounts

See the connected accounts and whether each one works. Archived accounts are not listed. Scripts and agents list them to find the accounts to publish to.
