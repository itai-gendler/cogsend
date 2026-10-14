---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls cancel_delivery
    kind: actor
    actor: ai-agent
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
  - text: The Product cancels the delivery
    kind: product
    actor: ai-agent
    entities:
      - { entity: delivery, effect: changes, from: Scheduled, to: Cancelled, facts: [] }
    contexts: { mcp: { place: mcp } }
---

# Cancel a delivery from an AI agent

## Trigger

The Admin asks their agent to hold a post back.

## Outcome

That delivery will not go out.
