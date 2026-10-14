---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls update_draft with new text
    kind: actor
    actor: ai-agent
    entities: []
    contexts: { mcp: { place: mcp } }
  - text: The Product saves the post
    kind: product
    actor: ai-agent
    entities:
      - { entity: post, effect: changes, facts: [Text, Last edited] }
    contexts: { mcp: { place: mcp } }
---

# Edit a draft from an AI agent

## Trigger

The Admin asks their agent to rework a draft.

## Outcome

The post holds the agent's text.
