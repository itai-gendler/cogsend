---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls duplicate_draft
    kind: actor
    actor: ai-agent
    entities:
      - { entity: post, as: original, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
  - text: The Product creates a Draft copy and returns it
    kind: product
    actor: ai-agent
    entities:
      - { entity: post, as: copy, effect: creates, to: Draft, facts: [Title, Text, Selected accounts, Last edited] }
    contexts: { mcp: { place: mcp } }
---

# Duplicate from an AI agent

## Trigger

The Admin asks their agent to post something again next week.

## Outcome

A new draft copy exists.
