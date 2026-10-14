---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls delete_draft
    kind: actor
    actor: ai-agent
    entities: []
    contexts: { mcp: { place: mcp } }
  - text: The Product deletes the post with its images and overrides
    kind: product
    actor: ai-agent
    entities:
      - { entity: post, effect: removes, from: Draft }
      - { entity: image, effect: removes, with: post }
      - { entity: platform-override, effect: removes, with: post }
    contexts: { mcp: { place: mcp } }
---

# Delete from an AI agent

## Trigger

The Admin asks their agent to throw a draft away.

## Outcome

The draft is gone.
