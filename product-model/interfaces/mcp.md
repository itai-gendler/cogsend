---
type: agent
actors: [ai-agent]
entryPoints:
  - agent: /api/mcp
references:
  - { kind: doc, role: intent, target: docs/api.md, title: MCP server }
  - { kind: code, role: implementation, target: src/routes/api/mcp/+server.ts }
  - { kind: code, role: implementation, target: src/lib/server/mcp-auth.ts }
---

# MCP server

The Model Context Protocol server every instance answers at its own address,
through which an AI agent holding the Admin's personal API key works with
drafts and the publish queue.
