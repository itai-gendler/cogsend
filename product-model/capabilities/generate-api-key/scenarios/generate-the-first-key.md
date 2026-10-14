---
kind: primary
routes:
  web: Web
steps:
  - text: The Admin chooses Read-only or Read + write and presses Generate API key, then confirms
    kind: actor
    actor: admin
    entities:
      - { entity: api-key, effect: reads, facts: [] }
    contexts: { web: { place: web::app::settings } }
  - text: The Product creates an active API key with that scope and shows it once, keeping only its hash
    kind: product
    actor: admin
    entities:
      - { entity: api-key, effect: creates, to: Active, facts: [Prefix, Scope, Created] }
    contexts: { web: { place: web::app::settings } }
  - text: The Admin copies the key and presses I have saved it
    kind: actor
    actor: admin
    entities: []
    contexts: { web: { place: web::app::settings } }
---

# Generate the first key

## Trigger

The Admin wants a script or an agent to work without signing in.

## Outcome

An active key exists; Settings shows its prefix, scope, creation and last use.

## Edge cases

- Settings also shows the MCP endpoint and ready-made client configurations for Claude Code and Codex.
