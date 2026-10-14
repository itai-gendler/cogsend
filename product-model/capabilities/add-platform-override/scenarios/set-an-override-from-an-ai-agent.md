---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls set_draft_variant for a platform the post has no override for
    kind: actor
    actor: ai-agent
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
  - text: The Product creates the platform override for the post
    kind: product
    actor: ai-agent
    entities:
      - { entity: platform-override, effect: creates, facts: [Platform, Text] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
---

# Set an override from an AI agent

## Trigger

The Admin asks their agent for a shorter version for one platform.

## Outcome

The post has an override for that platform.
