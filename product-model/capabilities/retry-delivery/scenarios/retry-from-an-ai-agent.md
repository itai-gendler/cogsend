---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls retry_delivery
    kind: actor
    actor: ai-agent
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
  - text: The Product sends the delivery again and returns the result
    kind: product
    actor: ai-agent
    entities:
      - { entity: delivery, effect: changes, from: Failed, to: Published, facts: [Error, Attempts, Link] }
    contexts: { mcp: { place: mcp } }
---

# Retry from an AI agent

## Trigger

The Admin asks their agent to retry what failed.

## Outcome

The delivery is published.
