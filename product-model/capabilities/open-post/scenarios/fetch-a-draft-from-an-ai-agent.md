---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls get_draft
    kind: actor
    actor: ai-agent
    entities: []
    contexts: { mcp: { place: mcp } }
  - text: The Product returns the post with its overrides and deliveries
    kind: product
    actor: ai-agent
    entities:
      - { entity: post, effect: reads, facts: [Text] }
      - { entity: platform-override, effect: reads, facts: [Platform, Text] }
      - { entity: delivery, effect: reads, facts: [Scheduled time, Error] }
    contexts: { mcp: { place: mcp } }
---

# Fetch a draft from an AI agent

## Trigger

The agent needs a post before changing it.

## Outcome

The agent has the post.
