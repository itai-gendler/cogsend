---
kind: primary
routes:
  mcp: MCP
steps:
  - text: The AI agent calls publish_draft for a draft and an account
    kind: actor
    actor: ai-agent
    entities:
      - { entity: account, effect: reads, facts: [] }
    contexts: { mcp: { place: mcp } }
  - text: The Product queues a delivery and sends the post
    kind: product
    actor: ai-agent
    entities:
      - { entity: delivery, effect: creates, to: Queued, facts: [Attempts] }
      - { entity: post, effect: reads, facts: [Text] }
    contexts: { mcp: { place: mcp } }
  - text: The platform accepts it and the Product returns the result
    kind: product
    actor: ai-agent
    entities:
      - { entity: delivery, effect: changes, from: Queued, to: Published, facts: [Link] }
      - { entity: post, effect: changes, from: Draft, to: Published, facts: [] }
    contexts: { mcp: { place: mcp } }
---

# Publish from an AI agent

## Trigger

The Admin tells their agent to post a draft now.

## Outcome

The post is published on that account.

## Edge cases

- The tool is marked as one that publishes; only the agent's client can stop and ask first.
