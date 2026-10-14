---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls list_drafts or list_queue
    kind: actor
    actor: ai-agent
    entities: []
    contexts: { mcp: { place: mcp } }
  - text: The Product returns the posts and their deliveries
    kind: product
    actor: ai-agent
    entities:
      - { entity: post, effect: reads, facts: [Title, Text] }
      - { entity: delivery, effect: reads, facts: [Scheduled time, Error] }
    contexts: { mcp: { place: mcp } }
---

# List drafts from an AI agent

## Trigger

The Admin asks their agent what is scheduled this week.

## Outcome

The agent has the list.
