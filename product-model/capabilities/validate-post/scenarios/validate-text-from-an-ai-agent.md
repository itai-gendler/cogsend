---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls validate_post with a text
    kind: actor
    actor: ai-agent
    entities:
      - { entity: post, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
  - text: The Product answers with its length per platform and any issues
    kind: product
    actor: ai-agent
    entities: []
    contexts: { mcp: { place: mcp } }
---

# Validate text from an AI agent

## Trigger

An agent checks a draft it wrote.

## Outcome

The agent can shorten the text before saving it.
