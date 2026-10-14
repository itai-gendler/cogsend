---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls delete_draft_variant for a platform
    kind: actor
    actor: ai-agent
    entities: []
    contexts: { mcp: { place: mcp } }
  - text: The Product removes the platform override
    kind: product
    actor: ai-agent
    entities:
      - { entity: platform-override, effect: removes }
      - { entity: post, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
---

# Delete an override from an AI agent

## Trigger

The Admin asks their agent to drop a tailored version.

## Outcome

That platform gets the Global text.
