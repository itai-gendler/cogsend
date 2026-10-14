---
kind: system
acts: external
references:
  - { kind: doc, role: intent, target: docs/api.md, title: MCP server }
  - { kind: code, role: implementation, target: src/routes/api/mcp/+server.ts }
---

# AI agent

An agent harness the Admin connects to the MCP server with their personal API
key, such as Claude Code or Codex, to read, draft, schedule and publish posts
for them.
