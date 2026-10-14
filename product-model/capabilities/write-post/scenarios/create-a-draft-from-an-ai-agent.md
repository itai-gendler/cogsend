---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls create_draft with the text
    kind: actor
    actor: ai-agent
    entities: []
    contexts: { mcp: { place: mcp } }
  - text: The Product creates a Draft post and returns it
    kind: product
    actor: ai-agent
    entities:
      - { entity: post, effect: creates, to: Draft, facts: [Title, Text, Last edited] }
    contexts: { mcp: { place: mcp } }
---

# Create a draft from an AI agent

## Trigger

The Admin asks their agent to draft a post.

## Outcome

A Draft post exists in CogSend for the Admin to review.
