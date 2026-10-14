---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls list_connections
    kind: actor
    actor: ai-agent
    entities: []
    contexts: { mcp: { place: mcp } }
  - text: The Product returns the connected accounts
    kind: product
    actor: ai-agent
    entities:
      - { entity: account, effect: reads, facts: [Platform, Handle] }
    contexts: { mcp: { place: mcp } }
---

# List accounts from an AI agent

## Trigger

An agent needs to know where it can post.

## Outcome

The agent knows the accounts.
