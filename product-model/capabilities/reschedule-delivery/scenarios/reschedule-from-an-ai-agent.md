---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls reschedule_delivery with a new time
    kind: actor
    actor: ai-agent
    entities:
      - { entity: delivery, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
  - text: The Product moves the delivery to that time
    kind: product
    actor: ai-agent
    entities:
      - { entity: delivery, effect: changes, facts: [Scheduled time, Attempts] }
    contexts: { mcp: { place: mcp } }
---

# Reschedule from an AI agent

## Trigger

The Admin asks their agent to push a post back an hour.

## Outcome

The delivery waits for its new time.
