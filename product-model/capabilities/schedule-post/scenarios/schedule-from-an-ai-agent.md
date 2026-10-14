---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls schedule_draft with accounts and a time
    kind: actor
    actor: ai-agent
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
  - text: The Product schedules a delivery for each account
    kind: product
    actor: ai-agent
    entities:
      - { entity: delivery, effect: creates, to: Scheduled, facts: [Scheduled time, Attempts] }
      - { entity: post, effect: changes, from: Draft, to: Scheduled, facts: [] }
      - { entity: account, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
---

# Schedule from an AI agent

## Trigger

The Admin asks their agent to schedule a post for tomorrow morning.

## Outcome

The post waits for its time.
