---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls set_draft_variant for a platform the post already overrides
    kind: actor
    actor: ai-agent
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
  - text: The Product saves the platform override
    kind: product
    actor: ai-agent
    entities:
      - { entity: platform-override, effect: changes, facts: [Text] }
      - { entity: post, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
---

# Change an override from an AI agent

## Trigger

The Admin asks their agent to rewrite one platform's version.

## Outcome

That platform gets the agent's text.
